The WPD pack files (not to be confused with the WDB files), is like a mini archive that can hold a lot of files inside it. they come in .bin, .wpd, .wpk, .xgr, .xfv, .xwb, and .xwp file extensions.
<br><br>Sometimes these files can also have a paired [IMGB](https://lr-research-team.github.io/wiki/file-formats/model-texture-formats/imgb/) file which can contain header less DDS texture or image related data for all txbh files ([SEDBtxb](https://lr-research-team.github.io/wiki/file-formats/model-texture-formats/trb/#sedbtxb) section only data), that are packed inside this archive file.

# Section Header

N.B.: The below sections are all in Big Endian.

#### WPD Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | String | FourCC, Always WPD ("White Packed Data") |
| 0x4 | 0x4 | UInt32 | File count |
| 0x8 | 0x8 | UInt32[2] | Reserved, always null |

#### WPD File info section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x10 | 0x10 | String | File Name, null bytes are added if length is less than 0x10 |
| 0x20 | 0x4 | UInt32 | File data start offset | 
| 0x24 | 0x4 | UInt32 | File size | 
| 0x28 | 0x4 | String | File's Extension |
| 0x2C | 0x4 | UInt32 | Reserved, always null |