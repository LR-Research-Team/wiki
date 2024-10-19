SCD is a sound container file format that is used in the trilogy for storing all of its audio files. the underlying audio stream can be of different formats like Vorbis, MP3, XMA, or ADPCM. this wiki mainly focuses on the PC version SCDs, which store the audio streams in Vorbis (for music) and ADPCM (for sfx and voiceovers). 

<br>**Important:** The bytes have to be read in Little Endian for the PC version files and in Big Endian for the console version files.

### Main Header section
| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | FourCC. Always 0x53454442 (SEDB, "Section Data Binary") |
| 0x4 | 0x4 | UInt32 | Resource FourCC, always SSCF |
| 0x8 | 0x4 | UInt32 | Unknown (Version ?, always 3) |
| 0xC | 0x2 | UInt16 | Unknown, always 1024 |
| 0xE | 0x2 | UInt16 | Unknown, always 48 |
| 0x10 | 0x8 | UInt64 | File size |
| 0x18 | 0x8 | UInt64 | Reserved, always null |
| 0x20 | 0x8 | UInt64 | Reserved, always null |
| 0x28 | 0x8 | UInt64 | Reserved, always null |

### Sub Header section

N.B.: The sub header begins from offset 0x30 onwards. as some parts of the sub header are not properly reversed, they are marked as unknown. offsets given in the **_Offset_** coloumns are all relative from the sub header start, while the offsets given in the **_Description_** columns are absolute.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x2 | UInt16 | Number of 'A' chunks |
| 0x3 | 0x2 | UInt16 | Number of 'B' chunks |
| 0x4 | 0x2 | UInt16 | Number of 'Stream-info' chunks |
| 0x6 | 0x2 | UInt16 | Numbered sound folder id |
| 0x8 | 0x4 | UInt32 | [Chunk-B table offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-b-table) |
| 0xC | 0x4 | UInt32 | [Stream-info table offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info-table) |
| 0x10 | 0x4 | UInt32 | Chunk-C table offset |
| 0x14 | 0x4 | UInt32 | Reserved, always null |
| 0x18 | 0x4 | UInt32 | Chunk-D table offset |
| 0x30 | 0x4 | UInt32 | SCD File number, sometimes present when there are multiple streams |

#### Chunk-A table

This table begins from 0x50 (absolute) onwards and would contain 4 offsets for each Chunk-A chunk in this file. music files (Vorbis type) will have just one Chunk-A chunk which means one Chunk-A chunk offset, while the non music files (ADPCM type) can have more than one Chunk-A chunks. the secondary offsets will be null if there is only one Chunk-A chunk.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x50 | 0x4 | UInt32 | [Chunk-A chunk offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-a) |

#### Chunk-B table

This table begins after the Chunk-A table and would contain 4 offsets for each Chunk-B chunk in this file.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x00 | 0x4 | UInt32 | [Chunk-B chunk offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-b) |

#### Stream Info table

Depending on the number of stream info offsets, there should be a UInt32 offset for each sound stream info in the file. music files (Vorbis type) will have just one stream which means one stream info offset, while the non music files (ADPCM type) can have more than one stream so more than one stream info offset. do note that there can be info offsets that lead to dummy data or offset that do not have a valid audio stream related info.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x00 | 0x4 | UInt32 | [Stream Info offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info) |

#### Chunk-C table

This table begins after the Stream Info table and would contain 4 offsets for each Chunk-C chunk in this file. as of now there is no way to determine how many of these chunks are present in a SCD file.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x00 | 0x4 | UInt32 | [Chunk-C chunk offset](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-c) |
<br>


### Chunk-A

The Chunk-A offset is given in the [Chunk-A table](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-a-table).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x3 | char[3] | Unknown |
| 0x4 | 0x1 | UInt8 | Switching tracks flag, see [Switching tracks flag info](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#switching-tracks-flag) |
| 0x8 | 0x4 | Float32 | SCD volume, volume of the file ingame |
| 0x12 | 0x2 | UInt16 | SCD file number, part of the filecode |

The file number is sometimes not present if there are multiple streams in the SCD file.

### Chunk-B

The Chunk-B offset is given in the [Chunk-B table](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-b-table). as of now this chunk is not properly reversed.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |

### Stream Info

The info section offset is given in the [Stream Info table](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info-table).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Audio stream size |
| 0x4 | 0x4 | UInt32 | Number of Channels |
| 0x8 | 0x4 | UInt32 | Sample Rate |
| 0xC | 0x4 | UInt32 | Format flag, see [Flag info](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd#flag-info) |
| 0x10 | 0x4 | UInt32 | Loop Start |
| 0x14 | 0x4 | UInt32 | Loop End |
| 0x18 | 0x4 | UInt32 | [Partial Header/XOR chunk](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#partial-headerxor-chunk) size |

### Chunk-C

The Chunk-C offset is given in the [Chunk-C table](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#chunk-c-table). as of now this chunk is not properly reversed.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |

### Switching tracks flag

An UInt8 value is used to determine whether the SCD file switches to play the secondary track from the top and bottom channels, when enemies appear onscreen. 

| Value | Description |
| --- | --- |
| 1 | normal stereo channel scd file |
| 2 | multi track quad channel scd file |

### Flag info

An UInt32 value is used to determine the format of the underlying audio stream that is stored inside the SCD file. 

| Value | Description |
| --- | --- |
| 6 | Vorbis |
| 7 | Mpeg3 |
| 11 | XMA2 |
| 12 | ADPCM |

### Partial Header/XOR chunk
This chunk begins 4 bytes after its size offset in the [Stream Info](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info) and varies according to the game and the type of audio stream. do note that only the Partial Header chunk for ADPCM type stream is given.
- If this is a Vorbis type stream from Final Fantasy XIII, then this chunk would have to be considered as a Partial Header and is not required for audio extraction and replacement.

- If this is a Vorbis type stream from Final Fantasy XIII-2 and Lightning Returns: Final Fantasy XIII, then this would be considered as a XOR chunk which is required for audio extraction. 

- For ADPCM streams from the trilogy, you have to consider this chunk as a Partial Header and use it for audio extraction and replacement.

**Partial Header chunk (ADPCM)**

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x2 | UInt16 | ADPCM format tag, always 2 |
| 0x3 | 0x2 | UInt16 | Number of Channels, same as in Info section |
| 0x4 | 0x4 | UInt32 | Sample Rate, same as in Info section |
| 0x8 | 0x4 | UInt32 | Average bytes per sample |
| 0xC | 0x2 | UInt16 | Block align |
| 0xE | 0x2 | UInt16 | Bits per Sample, always 4 |
| 0x10 | 0x2 | UInt16 | CbSize, always 32 |
| 0x12 | 0x2 | UInt16 | Samples per block |
| 0x14 | 0x2 | UInt16 | Number of entries in Coefficients, always 7 |
| 0x16 | 0x1C | Char | Array of compression coefficients, always common |

<br>**ADPCM Compression Coefficients:** 
<br>These byte values are always common and each one should be parsed as an UInt16 and Int16 (signed) accordingly. if you are just extracting the audio file, then you can just copy paste all the 28 bytes of this array into your extracted audio file with a valid ADPCM header.


<br>**XOR chunk (Vorbis only)**

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x2 | UInt16 | Encryption flag, always 8194 |
| 0x2 | 0x1 | UInt8 | UnXOR magic number |
| 0x3 | 0x1 | UInt8 | Reserved, always null |
| 0x4 | 0x4 | UInt32 | Reserved, always null |
| 0x8 | 0x4 | UInt32 | Unknown |
| 0xC | 0x4 | UInt32 | Unknown, always 1036831949 |
| 0x10 | 0x4 | UInt32 | Ogg page table size |
| 0x14 | 0x4 | UInt32 | Vorbis Header size, also applies for the XOR'ed data |
| 0x18 | 0x4 | UInt32 | Unknown |
| 0x1C | 0x4 | UInt32 | Unknown |

The rest of the data in this chunk are the ``OggS`` page offsets and the XOR'ed vorbis header. each page offset will lead to the start of an ``OggS`` page in the audio stream data while the XOR'ed vorbis header data has to be UnXOR'ed to get a valid vorbis header for the audio stream data. 

You can get the relative start position of the XOR'ed header data from this MetaData/Encoder/XOR chunk with this formulae: 
<br>XOR'ed data start = Ogg page table size + 32 

Refer to the [UnXOR'ing logic](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#unxoring-logic) for UnXOR'ing the header data.


### Audio stream info
Vorbis type streams have the audio header, while the ADPCM ones do not. you have to manually generate a WAV ADPCM header with the necessary info given in the [Stream Info Section](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info) and the [Partial Header/XOR Chunk](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#partial-headerxor-chunk).
<br><br>
**Conversion Notes:**

- Vorbis streams from the game aren't serialized. if you are trying to replace an existing vorbis type SCD file, then ensure that your vorbis converter doesn't serialize the converted audio file. you can use the **_VorbisEncoder_** tool that comes with the **_NovaChrysalia_** Mod manager to convert your audio track to vorbis. make sure to update the offsets in the [Stream Info Section](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#stream-info) to reflect your new vorbis file.

- If you are trying to replace an existing ADPCM type SCD file, then you have to strip the WAV header from your encoded file as well as update the number of channels, sample rate, average bytes per sample, block align, and the samples per block offsets in the [Partial Header/XOR chunk](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#partial-headerxor-chunk). the values that you have to put in these offsets can all be found in your newly encoded ADPCM file's header.
<br>

#### UnXOR'ing logic
Final Fantasy XIII-2 and Lightning Returns: Final Fantasy XIII have its Vorbis type stream's header XOR'ed. you would have to use this following logic below to decrypt the header.
<br><br>
We will use the file "music_Academia.win32.scd" from Final Fantasy XIII-2 JP audio data as an example to explain the logic.

- Lets take the UnXOR magic number from the [Partial Header/XOR chunk](https://lr-research-team.github.io/wiki/file-formats/audio-format/scd/#partial-headerxor-chunk) of this file. this number will be ``0x36``. 

- Go to the XOR'ed data start position in this file and take the first byte here which will be ``0x79``.

- XOR ``0x79`` with the magic number ``0x36`` and we get ``0x4F``. this would be our first UnXOR'ed vorbis header byte.

- Do the same for the rest of the bytes in the XOR'ed data and once you have completely UnXOR'ed the data, copy the UnXOR'ed bytes into a new empty file. 

- Now copy the audio stream data after the UnXOR'ed bytes into this new file and save the file with a ``.ogg`` extension. this should now allow you to open/play the file in any media player that supports the vorbis audio format.