These are the main archive files that contain all of the game's data and always have a paired filelist file. the filename for this archive type have "white" in their filenames along with a platform code (.win32, .ps3, and .x360). 
<br><br>The filelist file structure is the only thing that you would need to know if you want to extract or repack files from the white BIN archive and so only the structs for that is given here.

# Final Fantasy XIII

#### Filelist Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Chunk Info start Offset |
| 0x4 | 0x4 | UInt32 | Chunk data start offset |
| 0x8 | 0x4 | UInt32 | Total number of files |

#### File Entry section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | The File Code |
| 0x4 | 0x2 | UInt16 | Chunk number in which the file info string is stored |
| 0x6 | 0x2 | UInt16 | Position of the file info string in the chunk |

The filecode contains information that determines how the game is supposed to parse the file. this code contains info that determine the file type, the file id or number, and its category or group.

#### Chunk Info section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Chunk Uncompressed size |
| 0x4 | 0x4 | UInt32 | Chunk Compressed size |
| 0x8 | 0x4 | UInt32 | Chunk position, relative from Chunk data start offset |

A chunk is a collection of file path strings that contain the filepath, file position, and the size of the file inside the white BIN archive. each chunk is zlib compressed and you would have to decompress it to get readable file path strings.<br><br>

#### Chunk Data section
Here is how a single decompressed file path string looks like:
```
64:1000:2f5:mot/pc/sk_c005_va/t1.white.win32.bin
```
The ```:``` is used to separate the data into multiple parts and all of the numerical values at the first three parts would have to be converted from hexadecimal to decimal

#### Path string structure
| Value | Info | Description |
| --- | --- | --- |
| 0x64 | File Position in the white BIN archive | Multiply this value with 0x800 | 
| 0x1000 | Uncompressed file size | Actual file size |
| 0x2F5 | Compressed file size | Size of the file when its zlib compressed, this is the size of the file when stored in the archive |
| mot/pc/sk_c005_va/t1.white.win32.bin | Virtual path | The virtual path string |

Most of the files inside the white BIN archive are compressed with zlib compression while few of the files aren't compressed. if the uncompressed and the compressed values given in the string is similar, then that file is not compressed in the archive. 

When rebuilding the archive, you have to ensure that the position at which you are placing a file is divisible by 0x800. if the position isn't divisible, then add some null bytes till the next closest divisible by 0x800 position value.


# Final Fantasy XIII-2 and Lightning Returns: Final Fantasy XIII

The filelist files of XIII-2 and Lightning Returns are encrypted and due to the presence of the encryption's header, the filelist header section and the rest of the important data starts from position 0x20 onwards. the main header and the chunk info sections contain the same info as the first game with the only difference being in the File Entry section. 

The filelist file has to be decrypted with the [WhiteCryptTool](https://github.com/Surihix/WhiteCryptTool) first before you begin reading the necessary offsets. do note that some of the filelist files aren't encrypted and you can determine this by checking if the below encryption header is present in the filelist file.

#### Filelist Encryption header
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | UInt32[4] | Encryption Seed, MD5 hash of the decrypted filelist data |
| 0x10 | 0x4 | UInt32 (BE) | Filelist data size |
| 0x14 | 0x4 | UInt32 | Encryption tag. value is always 501232760 |
| 0x18 | 0x8 | UInt32[2] | Reserved, always null |

Note: The MD5 hash is just for the decrypted filelist data without the additional padding at the end of the filelist data, as well as without the [Filelist Encryption Header](#filelist-encryption-header) and [Filelist Encryption Footer](#filelist-encryption-footer) sections.

#### Filelist Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x20 | 0x4 | UInt32 | Chunk Info start Offset |
| 0x4 | 0x4 | UInt32 | Chunk data start offset |
| 0x8 | 0x4 | UInt32 | Total number of files |

These offsets have to be taken relatively from position 0x20 onwards due to the encryption header (eg. 0x20 + Chunk Info start offset, 0x20 + Chunk data start offset).
<br>

#### File Entry section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | The File Code |
| 0x4 | 0x2 | UInt16 | Position of the file info string in the chunk |
| 0x6 | 0x1 | UInt8 | Chunk number in which the file info string is stored |
| 0x7 | 0x1 | UInt8 | File type ID |

The position value of the file info string in the odd number chunks, will start from 32768 onwards and resets to 0 after an odd numbered chunk. it again starts from 32768 for the next odd numbered chunk and again switches back to 0 after that chunk. 

You have to take the actual position value of the file path string in the chunk and add it to 32768. the resulting value will be the position value in this Entry section.

For example 32768 would be position 0, 32819 would be position 51 and so on. (32768 + 51 = 32819)
<br>

#### Filelist Encryption Footer

The following offsets are present at the end of the filelist file and is part of the encryption.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Filelist data size. same as the encryption header but in LE |
| 0x4 | 0x4 | UInt32 | Filelist checksum |

If you are rebuilding the filelist file, then make sure to update the filelist data size values present in the header, and footer sections. the MD5 hash need not be updated as the game directly uses those bytes in the header as a seed for the decryption process. the size of the filelist data has to be divisible by 8 and if its not divisible, then add some null bytes at the end to pad the size to the next closest divisible by 8 value. 

After you are done building the filelist, encrypt the file with WhiteCryptTool's encryption function. this will also calculate the checksum of the filelist before encrypting it.