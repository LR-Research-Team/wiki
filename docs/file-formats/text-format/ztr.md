ZTR (probably abbreviated as Zone Text Resource) is the text format used by the trilogy for storing all of its text data. each text or line has a corresponding text-id or line-id using which the game is able to display a text or line ingame. 

The string characters are stored in a compressed form which makes use of chunks that can be considered a dictionary. some of the string characters also denote special symbols or character combinations, that determine how a line is supposed to look when rendered ingame. see the [Encoding Keys Info](encoding-keys-info.md) section in this page for better understanding this concept.

This page will refer to the text and the ids as lines and line-ids respectively.
<br>

N.B.: The below sections are all in Big Endian.

### Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x8 | UInt64 | magicID, always 1 |
| 0x8 | 0x4 | UInt32 | Line count |
| 0xC | 0x4 | UInt32 | Decompressed line-ids size |
| 0x10 | 0x4 | UInt32 | Number of Dictionary chunk offsets |
<br>

### Dictionary chunk table

This offset table begins from 0x14 (absolute) onwards and would contain 4 offsets for each dictionary chunk in the file. 

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x50 | 0x4 | UInt32 | [Dictionary Chunk](#dictionary-chunk) offset |

There would be minimum two chunk offsets given in this table in any ZTR file. one offset for the line-ids dictionary chunk and the other for the line dictionary chunk.

The first offset would always be ``0`` and can be considered to be pointing to the first line-ids dictionary chunk. in some ZTR files, the line-ids can be stored in more than one dictionary chunk and the table will not have offsets for the secondary line-ids dictionary chunks. so you have to collectively consider these line-ids chunks as only one chunk.

The maximum amount of strings that a single dictionary chunk can hold is 4096 bytes and by using this size and the decompressed line-ids size in the [header](#header-section), you can compute how many chunks are used in total for storing the line-ids in the ZTR file. do note that the 4096 bytes is the amount of string data that is present in the Dictionary Chunk and its trailing [Compressed strings section](#compressed-strings). the next line-ids dictionary chunk would begin right after the first one's Compressed strings section has ended. 

The remaining offsets after the first 0 offset, will have to be taken relatively from the start of the first line dictionary chunk. (the line id chunk or chunks is located before this first chunk). lets say that the line-ids dictionary chunk ends at position 2428 and the second offset given in the table is ``2452``. by seeking 2452 bytes relatively from position 2428, you will reach the start of the second line dictionary chunk. now for the next line dictionary chunk offset, you have to go back to position 2428 and then seek according to the third offset value given in the table.
<br>


### Line Info table

This offset table begins after the dictionary chunk table and according to the line count in the header, there would be four offsets for each line in the file.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x1 | UInt8 | Dictionary Chunk number |
| 0x1 | 0x1 | UInt8 | Start position in page |
| 0x2 | 0x2 | UInt16 | Line's relative start position in the Compressed strings section |

Sometimes a line's starting string characters will begin in between a dictionary page. if the "Start position in page" value is lets say 2, then you have to take the characters from the dictionary page's second position onwards. as this is somewhat tricky to explain, its recommended to rebuild the dictionary pages in memory to make sense of this value. 
<br>

### Dictionary Chunk

This chunk has two sub chunks. a [Pages](#pages) chunk and a [Compressed strings](#compressed-strings) chunk

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Dictionary Size |
| 0x4 | Dictionary Size | String/Index value | Dictionary values |


#### Pages
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x1 | UInt8 | Page Index |
| 0x1 | 0x1 | UInt8 | First item (Page index / string character) |
| 0x2 | 0x1 | UInt8 | Second item (Page index / string character) |

The index value of the next page can sometimes skip one or two numbers. for instance after 7, the next page's index would be 9.

The First and Second item values have to be taken either as a page index number or as a string character. 
If the first and second items are matching with another page's index value, then the item's value has to be taken as a pointer to that another page and use the first and second item values from there as the string characters. the pointed page can further point to a previous page as well, so you have to somewhat rebuild the pages in memory when extracting the text data. 

For more information, refer to the [Decompression logic](#decompression-logic).
<br>

#### Compressed strings
This section contains decompressed string characters and pointers to a page index. if the string character value matches with a page index value, 
then you have to go to that page in the dictionary and get the string values present there.

#### Decompression logic
Let's say that a byte value in the [Compressed strings section](#compressed-strings) is ``4`` and there are 10 pages in the dictionary chunk above. each page has a index from 0 to 10. so you have to consider the value 4 as a pointer to the page with index 4 in the dictionary. 

Now in page 4 of the dictionary, the first item's value is 74 while the second item's value is 3. as there isn't a page with index 74, you have to take the string value associated with 74 which would be ``J``. the second item's value has to be considered as an index since there is a page with index 3. so go to page 3 and get both the first and second item values there which let's say are 111 and 121 respectively. as there aren't pages with index 111 and 121, you take the associated string values which would be ``o`` and ``y``. combine this together with the ``J`` value and you get the word ``Joy``.

Sometimes both the first and second item values can point to a page index which in turn can point to another page index as well. you have to go to the indexes in the order by which they are pointed, and get the first and second item values there. if an item's value is pointing to an index, it will always point to a previous page from that item's page.