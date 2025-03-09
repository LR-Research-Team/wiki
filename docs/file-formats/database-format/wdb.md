This is the main format used for all database files from the trilogy. the format structure is similar to the [WPD Pack files](../archive-formats/wpd-pack.md) with some minor differences.

# Section Header

N.B.: The below sections are all in Big Endian.

#### WDB Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | String | FourCC, Always WPD ("White Packed Data") |
| 0x4 | 0x4 | UInt32 | Record count |
| 0x8 | 0x8 | UInt32[2] | Reserved, always null |

#### WDB Record info section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x10 | 0x10 | String | Record Name, null bytes are added if string length is less than 0x10 |
| 0x20 | 0x4 | UInt32 | Record's data start offset | 
| 0x24 | 0x4 | UInt32 | Record's data size | 
| 0x28 | 0x8 | UInt32[2] | Reserved, always null |


## Database Structure
Each WDB file contains these common sections/records at the starting portion of the file. 

- [!!string](#string)

- [!!strtypelist](#strtypelist)

- [!!typelist](#typelist)

- [!!version](#version)

The structure underwent few changes in XIII-2 and LR where a section for the field names was introduced. this section gives information on how to parse each record's data and this being completely absent in XIII-1's wdb files, made parsing the wdb files from that game a bit difficult. the !!strtypelist section got changed to !!strtypelistb, while the !!typelist section will be present only when the !!strtypelist section is present.

These following new sections were introduced:

- [!!sheetname](#sheetname)

- [!structitem](#structitem)

- [!structitemnum](#structitemnum)

- [!!strArray](#strarray)

- [!!strArrayInfo](#strarrayinfo) 

- [!!strArrayList](#strarraylist)

Do note that the !!strArray, !!strArrayInfo and the !!strArrayList are only present in some of the WDB files. whenever there is a 4byte field, assume that the byte order is in Big Endian.

### !!string
This section contains strings (each terminated by a null value), used by each record stored in the WDB file. each record would contain one or more fields with a relative offset in this section. sometimes a record's string offset would point to a null terminator value in this section and this would indicate that the particular field in that record has no string.

### !!strtypelist
This section contains specific values that indicate how each 4bytes field of a record's data is supposed to be parsed. 

#### !!strtypelist structure

Each 4bytes field (UInt32) value in this section would contain these following parsing values. in the !!strtypelistb section (introduced from XIII-2 and LR), instead of using 4bytes, a single byte is used for storing the values.

| Value | Description | Comments |
| -- | -- | -- |
| 0 | Bitpacked data  | denotes more than one field or a single signed integer type field |
| 1 | Floating point type field | denotes a single field with a floating point value |
| 2 | !!string offset type field | denotes a single field with a UInt32 relative offset in the !!string section |
| 3 | UInt32 type field | denotes a single field with a UInt32 or Int32 value |

Do note that one of the ps3 version's WDB file, uses the same value `3` to also denote a 64bit unsigned integer.  

### !!typelist

This section is somewhat identical to the strtypelist section and contains values that indicates the data type for every 4bytes of a record's data. this section will not be present, if the file has a strtypelistb section (introduced from XIII-2 and LR). 

If there are multiple fields in a record's bitpacked data, the typelist section will contain more values and its size will be larger than the strtypelist section. if there are no multiple fields in the bitpacked data or if there is no bitpacked type data at all, then the typelist section will be identical to the strtypelist section. do note that the order in which these values are present in this typelist section can be random especially when there are multiple fields inside a bitpacked data. 

#### !!typelist structure

Each 4bytes field (UInt32) value in this section would contain these following values:

| Value | Description | Comments |
| -- | -- | -- |
| 0 | Signed integer value field | denotes a single field with a signed integer value |
| 1 | Floating point value field | denotes a single field with a floating point value |
| 2 | !!string offset type field | denotes a single field with an UInt32 offset in the !!string section |
| 3 | Unsigned integer type field | denotes a single field with an unsigned integer value |

The type `1` value, would denote a signed integer value for fields that are inside a bitpacked data. a possible theory as to why these types of fields share the same `1` value as the floating point type fields could be due to the game using the values from these fields as floats at runtime.

#### Structure notes
This section can also be used to roughly determine how many fields are present for each records in the wdb file. 

For example, consider a scenario where the values in the strtypelist are `0`, `2`, `2`, and `3`, while the values in the typelist section are `2`, `2`, `3`, `3`, `3`, `3`, and `3` respectively. 

The first value `0` in the strtypelist section indicates a bitpacked data and if you look among the values in the typelist section, you would see there are five `3` values. 

We know that this value indicates an unsigned integer type field and so we would have to assume that there are five unsigned integer type fields for the records. since there is already one unsigned integer type field being denoted by the strtypelist section, we can easily mark four bytes among the record's data. now there are still four more fields remaining, and so we have to consider that they are all inside the bitpacked data. the remaining `2` would indicate !!string offset type fields and this way we have established how many fields are present for each record.

In a different scenario, if the strtypelist section is similar to the typelist section and both of them contain a value `0`, then you have to consider the `0` value in the strtypelist section to denote a single signed integer type field.

### !!version
This section contains a single UInt32 value that potentially holds some sort of a version number or id. 

### !!sheetname
This section contain a string (null terminated), that gives a brief idea about the type of records that are stored in the WDB file.

### !structitem
The section contains one or more strings (each null terminated) which are all the field names for each record's data, stored in the WDB file. refer to this [page](../database-format/wdb-field-names.md) for more information.

### !structitemnum
This section contains a UInt32 value that indicates the total number of fields used in the WDB file. you can use this value to determine the number of field names, present in the !structitem section.

### !!strArray
This section contains value arrays that are bitpacked offset values to strings present in the !!string section. the number of bitpacked `s#` fields would indicate the number of arrays present in this section. the !!strArrayInfo section would contain the necessary information on how to parse each value in this section while the !!strArrayList contains the relative start offset of each array present in this section. 

To make it easy to understand, here is a small example.
Let's say there is a value `285212676` in the !!strArray section. the string offsets per value and the bits per value, given in the !!strArrayInfo section is `2` and `15` respectively. 

- Get the binary representation of `285212676`. it would be `00010001000000000000000000000100`.

- Since the string offsets per value is `2`, there are 2 string offset values stored in this binary value. let's split the binary value according to the bits per value number which would be `15`. we must begin splitting the binary value from the last value onwards. 

- After splitting, we will get `000000000000100` and `010001000000000`. the remaining binary numbers can be discarded.

- `000000000000100` and `010001000000000` in numerical forms would be `4` and `8704` respectively. these are our `2` offsets in the !!string section.

- Consider the two string values present in those `2` offsets as items in the current array. their indexes would be `1` and `0` and these index values would be what a record's `s#` field value would indicate.

- The next value's two indexes in the current array would be `3` and `2`. the index values have a right to left order.


### !!strArrayInfo
This section is always 4bytes in size and contains values that determine the general structure of each value present in the !!strArray section.

#### !!strArrayInfo structure
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x1 | UInt8 | Reserved, always null |
| 0x1 | 0x1 | UInt8 | Reserved, always null |
| 0x2 | 0x1 | UInt8 | Number of string offsets per value in !!strArray |
| 0x3 | 0x1 | UInt8 | Number of bits per value in !!strArray |

### !!strArrayList
This section contains the relative start offsets of each array present in the !!strArray section.
