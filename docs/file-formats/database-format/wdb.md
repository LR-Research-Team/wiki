This is the main format used for all database files from the trilogy. the format structure is similar to the [WPD Pack files](https://lr-research-team.github.io/wiki/file-formats/archive-formats/wpd-pack/) with some minor differences.

# Section Header

N.B.: The below sections are all in Big Endian.

#### WDB Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| FourCC, Always 0x57504400 (WPD, "White Packed Data") |
| 0x4 | 0x4 | UInt32| Record count |
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
- [!!string](https://github.com/LR-Research-Team/Datalog/wiki/WDB#string)
- [!!strtypelist](https://github.com/LR-Research-Team/Datalog/wiki/WDB#strtypelist)
- [!!typelist](https://github.com/LR-Research-Team/Datalog/wiki/WDB#typelist)
- [!!version](https://github.com/LR-Research-Team/Datalog/wiki/WDB#version)

The structure underwent few changes in XIII-2 and LR where a section for the field names was introduced. this section gives information on how to parse each record's data and this being completely absent in XIII-1's wdb files, made parsing the wdb files from that game a bit difficult. the !!strtypelist section got changed to !!strtypelistb, while the !!typelist section will be present only when the !!strtypelist section is present.

These following new sections were introduced:
- [!!sheetname](https://github.com/LR-Research-Team/Datalog/wiki/WDB#sheetname)
- [!structitem](https://github.com/LR-Research-Team/Datalog/wiki/WDB#structitem)
- [!structitemnum](https://github.com/LR-Research-Team/Datalog/wiki/WDB#structitemnum)
- [!!strArray](https://github.com/LR-Research-Team/Datalog/wiki/WDB#strArray)
- [!!strArrayInfo](https://github.com/LR-Research-Team/Datalog/wiki/WDB#strArrayInfo) 
- [!!strArrayList](https://github.com/LR-Research-Team/Datalog/wiki/WDB#strArrayList)

Do note that the !!strArray, !!strArrayInfo and the !!strArrayList are only present in some of the WDB files. whenever there is a 4byte field, assume that the byte order is in Big Endian.

### !!string
This section contains strings (each terminated by a null value), used by each record stored in the WDB file. each record would contain one or more fields with a relative offset in this section. sometimes a record's string offset would point to a null terminator value in this section and this would indicate that the particular field in that record has no string.

### !!strtypelist
This section contains specific values that indicate how each 4bytes field of a record's data is supposed to be parsed. 

Each 4bytes field (UInt32) value in this section would contain these following parsing values. in the !!strtypelistb section (introduced from XIII-2 and LR), instead of using 4bytes, a single byte is used for storing the values.

| Value | Description | Comments |
| -- | -- | -- |
| 0 | Bitpacked field | denotes more than one field or a single signed integer type field |
| 1 | Floating point type field | denotes a single field with a floating point value |
| 2 | !!string offset type field | denotes a single field with a UInt32 relative offset in the !!string section |
| 3 | UInt32 type field | denotes a single field with a UInt32 or Int32 value |

Do note that one of the ps3 version's WDB file, uses the same value `3` to also denote a 64bit unsigned integer.  

## !!typelist
This section is somewhat identical to the strtypelist section and contains values that indicates the field type. this section will not be present if the file has a strtypelistb section (introduced from XIII-2 and LR). 

If there are multiple fields in a record's bitpacked field, the typelist section will contain more values and its size will be larger than the strtypelist section. if there are no multiple fields in the bitpacked field or if there is no bitpacked field at all, then the typelist section will be identical to the strtypelist section. the order in which these values are present in this section can be random especially when there are bitpacked fields and this section can be used to determine how many signed and unsigned type fields are present in the bitpacked fields.

Each 4bytes field (UInt32) value in this section would contain these following values:
| Value | Description | Comments |
| -- | -- | -- |
| 0 | Signed integer value field | denotes a single field with a signed integer value |
| 1 | Floating point value field | denotes a single field with a floating point value |
| 2 | !!string offset type field | denotes a single field with an UInt32 offset in the !!string section |
| 3 | Unsigned integer type field | denotes a single field with an unsigned integer value |

## !!version
This section contains a single UInt32 value that potentially holds some sort of a version number or id. 

## !!sheetname
This section contain a string (null terminated), that gives a brief idea about the type of records that are stored in the WDB file.

## !structitem
The section contains one or more strings (each null terminated) which are all the field names for each record's data, stored in the WDB file. refer to this [page](https://github.com/LR-Research-Team/Datalog/wiki/WDB-Field-Names) for more information.

## !structitemnum
This section contains a UInt32 value that indicates the total number of fields used in the WDB file. you can use this value to determine the number of field names, present in the !structitem section.

## !!strArray
This section contains value arrays that are bitpacked offset values to strings present in the !!string section. the number of bitpacked `s#` fields would indicate the number of arrays present in this section. the !!strArrayInfo section would contain the necessary information on how to parse each value in this section while the !!strArrayList contains the relative start offset of each array present in this section. 

To make it easy to understand, here is a small example.
Let's say there is a value `285212676` in the !!strArray section. the string offsets per value and the bits per value, given in the !!strArrayInfo section is `2` and `15` respectively. 

- Get the binary representation of `285212676`. it would be `00010001000000000000000000000100`.

- Since the string offsets per value is `2`, there are 2 string offset values stored in this binary value. let's split the binary value according to the bits per value number which would be `15`. we must begin splitting the binary value from the last value onwards. 

- After splitting, we will get `000000000000100` and `010001000000000`. the remaining binary numbers can be discarded.

- `000000000000100` and `010001000000000` in numerical forms would be `4` and `8704` respectively. these are our `2` offsets in the !!string section.

- Consider the two string values present in those `2` offsets as items in the current array. their indexes would be `1` and `0` and these index values would be what a record's `s#` field value would indicate.

- The next value's two indexes in the current array would be `3` and `2`. the index values have a right to left order.


## !!strArrayInfo
This section is always 4bytes in size and contains values that determine the general structure of each value present in the !!strArray section.
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x1 | UInt8 | Reserved, always null |
| 0x1 | 0x1 | UInt8 | Reserved, always null |
| 0x2 | 0x1 | UInt8 | Number of string offsets per value in !!strArray |
| 0x3 | 0x1 | UInt8 | Number of bits per value in !!strArray |

## !!strArrayList
This section contains the relative start offsets of each array present in the !!strArray section.
