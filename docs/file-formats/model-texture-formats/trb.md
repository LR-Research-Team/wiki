The TRB files are containers with various sections used to define the model (textures, shaders, skeleton, geometry etc). A binary template for this file format can be found [here](https://github.com/LR-Research-Team/010-binary-templates/tree/main/Model%20formats).

# Sections

## Section Header
The following header is for all the different sections.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| FourCC. Always 0x53454442 (SEDB, "Section Data Binary") |
| 0x4 | 0x4 | UInt32| Resource FourCC, gives the section type |
| 0x8 | 0x4 | UInt32 | Version |
| 0xC | 0x2 | UInt16 (BE) | Resource type 2, seems to define a subtype |
| 0xE | 0x2 | UInt16 | Header size, gives the section data offset |
| 0x10 | 0x4 | UInt32 | Section size, header included |
| 0x14 | 0x1C | UInt32[7] | Reserved, always null |

## Section Types

### SEDBRES

This section is used to define and encapsulate all the other ones. It contains information such as the sections count, offsets and other info. To avoid confusion, sections contained in this one will be called "subsections".

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/file-formats/model-texture-formats/trb/#section-header)| The header of this section |
| 0x30 | 0x4 | UInt32| File paths count, this should match the subsection count |
| 0x34 | 0x4 | UInt32| File paths offset, relative to the beginning of the first subsection |
| 0x38 | 0x4 | UInt32| Subsection count |
| 0x3C | 0x4 | UInt32| FourCC. Always 0x627274 (brt, "trb" in LE) |
| 0x40 | 0x10 x Subsection count | [Subsection Definition](https://lr-research-team.github.io/wiki/trb/#Subsection-Definition)[Subsection count] | Subsection offsets and lengths |

#### Subsection Definition

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| Subsection index, increments 1 by 1 |
| 0x4 | 0x4 | UInt32| Subsection offset, relative to the beginning of the first subsection |
| 0x8 | 0x4 | UInt32| Subsection size |
| 0xC | 0x4 | UInt32| Subsection type 2 (not sure) |

--------------------------------

### SEDBtxb

This section is used to define a single texture (so each texture used by the model will have an associated SEDBtxb section).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | 0x4 | UInt32| GTEX Chunk offset ?  |
| 0x34 | 0xC | UInt32[3]| Reserved, always null |
| GTEX Chunk Offset | Variable | [GTEX](https://lr-research-team.github.io/wiki/trb/#gtex)| GTEX Chunk |

N.B.: The SEDBtxb section is 16 bytes aligned, some 0 padding is used to properly align if necessary.

#### GTEX

N.B.: This chunk is in Big Endian.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| FourCC. Always 0x47544558 (GTEX), Game Texture? |
| 0x4 | 0x2 | UInt16| Version |
| 0x6 | 0x1 | UInt8 | [Texture format](https://lr-research-team.github.io/wiki/trb/#texture-format) |
| 0x7 | 0x1 | UInt8 | Mipmap Count |
| 0x8 | 0x1 | UInt8 | Unknown (srgb flag or something ?) |
| 0x9 | 0x1 | UInt8 | [Texture type](https://lr-research-team.github.io/wiki/trb/#texture-format) |
| 0xA | 0x2 | UInt16 | Width |
| 0xC | 0x2 | UInt16 | Height |
| 0xE | 0x2 | UInt16 | Depth |
| 0x10 | 0x4 | UInt32 | Mipmap information offset (relative to the GTEX start) |
| 0x14 | 0x4 | UInt32 | Reserved (always null) |
| Mip Info Offset | 0x8 x Mipmap Count | [Mipmap Specs](https://lr-research-team.github.io/wiki/trb/#mipmap-specs)[Mipmap Count] | The mipmaps' information |

#### Texture Format

| Value | Format |
| --- | --- | 
| 0x3 | R8G8B8A8 (Can have Mips)|
| 0x4 | R8G8B8A8 (No Mips)| 
| 0x18 | DXT1 | 
| 0x19 | DXT3 | 
| 0x1A | DXT5 |

#### Texture Type

| Value | Type | Description |
| --- | --- | --- |
| 0x0 | Classic | A Single texture |
| 0x1 | Cubemap | 6 textures with similar dimensions and mips |
| 0x2 | Stacked | XIII-LR only, multiple textures with similar dimensions |

#### Mipmap Specs

This struct defines the necessary information to extract the texture data from the associated **IMGB** file.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| Mip data offset (in the paired imgb file)|
| 0x4 | 0x4 | UInt32| Mip data size|

--------------------------------

### SEDBshd

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | Variable | [SHD](https://lr-research-team.github.io/wiki/trb/#SHD) | SHD Chunk |

--------------------------------

### SEDBmsst

This section is used to define the necessary semantics in case of data spread into several TRBs. The attribute definition is similar to the ones in the STMS chunk. See m253/583 on ps3/win32 for examples.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | Variable | [WPDContainer](https://lr-research-team.github.io/wiki/trb/#wpd-container) | Beginning of a WPD Container |

#### WPD Container

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| FourCC |
| 0x4 | 0x4 | UInt32| Record count |
| 0x8 | 0x8 | UInt32[2] | Reserved, always null |
| 0x10 | 0x20 | [WPDRecord](https://lr-research-team.github.io/wiki/trb/#WPD-Record)[Record count] | WPD record definitions |
| 0x10 + 0x20 x Record count | Variable | Binary | Data as per record definition| 

#### WPD Record

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | String | Name |
| 0x10 | 0x04 | UInt32 | Byte offset from end of the record definition |
| 0x14 | 0x04 | Uint32 | Length |
| 0x18 | 0x08 | String | Data type |

#### MSST Data

Data as defined by the STMS Header.  Matches the data format in the calling trb file.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x00 | 0x10 | [STMS Header](https://lr-research-team.github.io/wiki/trb/#stms-header) | Buffer Data Definition |
| 0x10 | [STMS Header]Attribute Count x 0x10 | [Attribute Info](https://lr-research-team.github.io/wiki/trb/#attribute-info)[Attribute count] | Attribute properties to parse the buffer |
| 0x10 + [STMS Header]Attribute Count x 0x10 | [STMS Header]Entry Count x [STMS Header]Stride | Variable | Buffer |

--------------------------------

### SEDBdepb

This section is used to reference another trb file with the missing data to build the model, only used when the data is spread into several TRBs.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | 0x2 | UInt16 | Section count |
| 0x32 | 0x2 | Uint16 | Model count (Typ. 1) |
| 0x34 | 0x4 | Uint16[2] | Reserved, always null | 
| 0x38 | 0x28 x Section count| [Remote Section](https://lr-research-team.github.io/wiki/trb/#remote-section)[Section count] | Section data|
| 0x38 + 0x28 x Section count| 0x20 | [Model Reference](https://lr-research-team.github.io/wiki/trb/#model-reference)[Model count] | Linked model names |

#### Section Data

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | String | Remote file name|
| 0x10 | 0x4 | String | Remote section type |
| 0x14 | 0x10 | String | Remote model (c_xxxx)|
| 0x24 | 0x4 | String | Remote model type |

#### Model Reference

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | String | This model name|
| 0x10 | 0x10 | String | Remote model name|

--------------------------------

### SEDBwrb

This section is used to define the geometry data (attributes, skinning information, submeshes etc).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | Variable | [WRB](https://lr-research-team.github.io/wiki/trb/#WRB) | WRB Chunk |

--------------------------------

### SEDBSKL

This section is used to define the model's skeleton.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | 0x4 | UInt32 | Subsections count |
| 0x34 | 0x4 | UInt32 | Name table offset |
| 0x38 | 0x4 | UInt32 | Names count |
| 0x3C | 0x4 | UInt32 | FourCC. Always 0x736B6C (skl in LE) |
| 0x40 | Subsections count * 0x10 | [SKL Subsection Header](https://lr-research-team.github.io/wiki/trb/#SKL-subsection-header)[Subsections count] | Subsections' headers |
| Variable | Variable | [SKL Subsections](https://lr-research-team.github.io/wiki/trb/#SKL-subsection) | The actual subsections|
| Name table offset | Variable | Stringz[names count] | Name table, with the joint names, type names, subsection names etc|

#### SKL Subsection Header

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Subsection name index (index in the name table, gives the purpose of the subsection) |
| 0x4 | 0x4 | UInt32 | Subsection start offset (relative to the end of the subsection headers) |
| 0x8 | 0x4 | UInt32 | Subsection end offset (relative to the end of the subsection headers) |
| 0xC | 0x4 | UInt32 | Unknown (always 1?) |

#### SKL Subsection

The subsections seen so far are the following:

##### **Hierarchy data subsection**

This subsection has the necessary information to construct the skeleton (parenting, position, rotation etc). The number of joint entries is equal to the subsection size divided by 0xB0 (size of the joint structure). The joint structure is defined the following way:

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| Name index (index in the name table) |
| 0x4 | 0x4 | UInt32| Type index (index in the name table)|
| 0x8 | 0x4 | UInt32| Unknown index (index in the name table, probably reserved)|
| 0xC | 0x4 | Int32| Always -1, probably padding |
| 0x10 | 0xC | Float32[3]| Joint location, in local space (i.e. relative to the parent joint) |
| 0x1C | 0x10 | Float32[4]| Joint rotation, in local space (i.e. relative to the parent joint). As a quaternion.|
| 0x2C | 0xC | Float32[3]| Joint scale, in local space (i.e. relative to the parent joint). Always (1,1,1) it seems.|
| 0x38 | 0x4 | Int32 | Parent index (index in the joint hierarchy)|
| 0x3C | 0x4 | Int32 | Child 1 index (index in the joint hierarchy)|
| 0x40 | 0x4 | Int32 | Child 2 index (index in the joint hierarchy)|
| 0x44 | 0x4 | UInt32 | Joint hash or joint index (For FF XIII)|
| 0x48 | 0x4 | UInt32 | Bitfield (assumption) of unknown purpose. Seen values: 0x2 (very common), 0x12 (XIII), 0x22 (LR garbs)|
| 0x4C | 0x4 | UInt32 | Group ID, referenced by animation files.|
| 0x50 | 0x60 | UInt32[24] | Reserved, always null.|

N.B. The child indices do not seem to be used within the game other than determining the load order of the bones.  Bones that are not 
listed in a “child” index are not created but the specific order of the child index does not seem to matter.  i.e. if each bone utilizes a single child index pointing to the next bone (0 -> 1, 1 -> 2, etc.) for the whole list, then it all still loads and works fine.  The only restriction is that a bone listed as a “parent” MUST be created before the parent index is used.  A parent or child index of -1 is not used.

For the group ID, the purpose seems to vary between the games: In XIII the joint groups seemed to be fairly well defined as

0 = Main
1 = Accessory/Clothing/Hair
2 = Body
3 = Head

Whereas in XIII-2/LR it seems to split the skeleton into "limbs".

##### **KineDriver subsection**

Research needed.

--------------------------------

### SEDBelb

This section is used to define the ["sockets"](https://docs.unrealengine.com/4.27/en-US/WorkingWithContent/Types/SkeletalMeshes/Sockets/), which are used as location to attach weapons, accessories etc.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x30 | [SectionHeader](https://lr-research-team.github.io/wiki/trb/#section-header)| The header of this section |
| 0x30 | 0x4 | UInt32| Socket count  |
| 0x34 | 0xC | UInt32[3]| Reserved, always null |

Next are some structs (socket count of them) used to define the names, bone parenting and location info of the sockets. 

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| Parent bone name offset (relative to the beginning of the SEDBelb section) |
| 0x4 | 0x4 | UInt32| Socket name offset (relative to the beginning of the SEDBelb section) |
| 0x8 | 0xC | Float32[3]| Socket location, in local space (i.e. relative to the parent bone) |
| 0x14 | 0xC | Float32[3]| Reserved, always null. May be padding. |

Next some euler angles (socket count of them), used to define the socket rotation.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | Float32| X axis rotation (in radians) |
| 0x4 | 0x4 | Float32| Y axis rotation (in radians) |
| 0x8 | 0x4 | Float32| Z axis rotation (in radians) |

Finally, a section where all the null-terminated strings referenced by the previous offsets are packed. Socket names and their bone parent names can be found here.

--------------------------------

### SEDBPHB

--------------------------------


# Chunks

Chunks are structures used to subdivide the above sections in several blocks of information. There are two chunk types : chunks and chunk containers. The latter are used to "pack" several chunks, which will be referred to as their "children".

## Chunks 

### Chunk Header

The following header is for all the different chunks.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32| FourCC, used to define the chunk |
| 0x4 | 0x4 | UInt32 | Version |
| 0x8 | 0x4 | UInt32 | Chunk Size (arbitrary, depending on the chunk it may be the size, size - 0xC, size - 0x4 etc)|
| 0xC | 0x4 | UInt32 | Next chunk offset (a 0 value means there's none) |

### FILE

This chunk contains the actual DX9 shader code and name. As of now the best way to disassemble/decompile the bytecode is to use the following [PR build](https://github.com/spacehamster/DXDecompiler/pull/10).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x4 | UInt32 | Shader block size (starting from the checksum, see below) |
| 0x14 | 0x4 | UInt32 | Shader name offset (relative to the chunk header's end)|
| 0x18 | 0x4 | UInt32 | Shader block offset (relative to the chunk header's end)|
| Shader name offset | Variable | Stringz | Shader name|
| Shader block offset | 0x10 | UInt8[16] | MD5 checksum of the shader bytecode|
| Shader block offset + 0x10| 0x4 | UInt32 | Shader bytecode length|
| Shader block offset + 0x14| 0x4 | UInt32 | Unknown|
| Shader block offset + 0x18| 0x8 | UInt32[2] | Reserved (always null ?)|
| Shader block offset + 0x20| Variable | Bytecode | DX9 shader bytecode|


### VCAP

The purpose of this chunk is currently unknown. It seems to always have the same size and content.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x4 | UInt32 | Unknow (always 4095 ?) |
| 0x14 | 0xC | UInt32[3] | Reserved ? (always null ?)|

### PCAP

The purpose of this chunk is currently unknown. It seems to always have the same size and content.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x80 | UInt32[32] | Unknow (always the same values ?) |

### PRAM

This chunk contains the shader parameter values and the samplers' data.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x2 | UInt16 | Unknown|
| 0x12 | 0x2 | UInt16 | Unknown|
| 0x14 | 0x4 | UInt32 | Unknown|
| 0x18 | 0x4 | UInt32 | Parameter count|
| 0x1C | 0x4 | UInt32 | The offset of a table containing the parameters' data offsets (relative to the chunk header's end)|
| 0x20 | 0x4 | UInt32 | The offset of a table containing the parameter names' offsets (relative to the chunk header's end)|
| 0x24 | 0x4 | UInt32 | Sampler count|
| 0x24 | 0x4 | UInt32 | The offset of a table containing the samplers' data offsets (relative to the chunk header's end)|
| 0x24 | 0x4 | UInt32 | The offset of a table containing the samplers' names' offsets (relative to the chunk header's end)|
| Parameter data offset table offset | parameter count x 0x4 | UInt32[parameter count] | Parameter data offset table|
| Parameter name offset table offset | parameter count x 0x4 | UInt32[parameter count] | Parameter names offset table|
| Sampler data offset table offset | sampler count x 0x4 | UInt32[sampler count] | Sampler data offset table|
| Sampler name offset table offset | sampler count x 0x4 | UInt32[sampler count] | Sampler names offset table|

A parameter data entry has the following structure:

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x2 | UInt16 | Boolean, 1 if it's a pixel shader parameter, 0 otherwise. |
| 0x2 | 0x4 | UInt16 | Data size, scalar if one, vec2/3/4 otherwise. |
| 0x4 | 0xC | UInt32[3]| Reserved, always null.|
| 0x10 | 0x10 | Float[4]| Data, always 4 floats (extra components zeroed out if needed)|

A sampler data entry has the following structure:

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x1 | UInt8 | Unknown (always 2 ?)|
| 0x1 | 0x2 | UInt8 | Unknown|
| 0x2 | 0x3 | UInt8 | String section size |
| 0x3 | 0x4 | UInt8 | Unknown|
| 0x4 | 0x1C | UInt32[7]| Unknown|
| 0x20 | Variable | Stringz[Variable]| String section (parsing logic tbd)|

### MDLC Header

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | Char[16] | Fixed size string|
| 0x20 | 0x24 | UInt32 | Unknown|
| 0x24 | 0x28 | UInt32 | MDL count|
| 0x28 | 0x2C | UInt32 | Unknown (bitfield, byte field ? Seen values : 0x1000000 in XIII, 0x3000000 in other games)|
| 0x2C | 0x30 | UInt32 | Reserved (always null ?)|

### MDL Header

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | Char[16] | Fixed size string, duplicate of the one in the NAME chunk above with a 16 char limit.|
| 0x20 | 0x24 | UInt32 | Unknown|
| 0x24 | 0x28 | UInt32 | MESH count|
| 0x28 | 0x2C | UInt32 | Unknown (bitfield, byte field ? Different values, possibly be four byte fields with the 3rd and 4th bytes always being 0.  1st and 2nd can have different values. (more so in the environment trb))|
| 0x2C | 0x30 | UInt32 | Reserved (always null ?)|

### MESH Header

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x1 | UByte | Unknown count|
| 0x11 | 0x1 | UByte | PGRP Chunk Count|
| 0x12 | 0x1 | UByte | STMS Chunk Count|
| 0x13 | 0x1 | UByte | ENVD Chunk Count|
| 0x14 | 0x4 | UInt32 | Shader index as loaded in memory ?|
| 0x18 | 0x2 | UInt16 | Vertex count|
| 0x1A | 0x2 | UInt16 | Face count|
| 0x1C | 0x4 | UInt32 | Reserved (always null ?)|

### NAME

This chunk stores a string. As its name suggests it's used to store a name.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | Variable | Stringz | The name stored in this chunk, either 0x10 or 0x20 padded|

### STR

This chunk stores a null terminated string. 

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | Stringz | The string stored in this chunk.|

### STMS

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | [STMS Header](https://lr-research-team.github.io/wiki/trb/#stms-header) | Buffer Data Definition |
| 0x20 | [STMS Header]Attribute Count x 0x10 | [Attribute Info](https://lr-research-team.github.io/wiki/trb/#attribute-info)[Attribute count] | Attribute properties to parse the buffer |
| 0x20 + [STMS Header]Attribute Count x 0x10 | [STMS Header]Entry Count x [STMS Header]Stride | Variable | Buffer - May not be present if trb data is found in another file. See [SEDBmsst](https://lr-research-team.github.io/wiki/trb/#SEDBmsst)|

#### STMS Header

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x2 | UInt16 | -1 if data found in another trb, 0 otherwise (see ps3 m583 TRB, paired with m253)|
| 0x2 | 0x2 | UInt16 | Attribute count |
| 0x4 | 0x4 | UInt32 | Entry count |
| 0x8 | 0x2 | UInt16 | MDL (6 bits) / MESH (5 bits) / STMS (5 bits) id |
| 0xA | 0x2 | UInt16 | Stride |
| 0xC | 0x2 | UInt16 | -1 if data found in another trb, offset in imgb otherwise if there is some (ps3)|
| 0xE | 0x1 | UByte | 1 if data in imgb, 0 if not |
| 0xF | 0x1 | UByte | Padding |

#### Attribute Info

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x4 | UInt32 | Offset (in the buffer) |
| 0x4 | 0x4 | UInt32 | [Data type](https://lr-research-team.github.io/wiki/trb/#data-type)|
| 0x8 | 0x4 | UInt32 | Count |
| 0xC | 0x2 | UInt16 | [Semantic](https://lr-research-team.github.io/wiki/trb/#semantic) |
| 0xE | 0x2 | UInt16 | Padding |

N.B.: For the bone indices, these are not the absolute indices as defined in the SEDBSKL section. Instead, a bone map is made using the ENVD chunks and the indices refer to the bones defined in the latter.

#### Data type

| Value | Data type |
| --- | --- | 
| 0x0 | UInt16 | 
| 0x1 | Float32 | 
| 0x2 | Float16 | 
| 0x3 | UByte | 
| 0x4 | Int16 | 
| 0x6 | Byte | 

#### Semantic

| Value | Semantic |
| --- | --- | 
| 0x0 | Position | 
| 0x2 | Normal | 
| 0x3 | Color | 
| 0x4 | Binormal | 
| 0x8 | UV1 | 
| 0x9 | UV2 |
| 0xA | UV3 |
| 0xB | UV4 |
| 0xD | Tangent |
| 0xE | Bone weight |
| 0xF | Bone index |
| 0xFF | Index |

N.B: Color : while this can be used to color shade the model somewhat, it's used more for shadowing areas of the model independently.  For example, Hope's wrists as they come out of his gloves are darkened by using this.  4 byte values, in RGBx.  255 being full brightness/color and lower values darkening the specific color. The game always keeps the last value at 255., which is most likely the alpha channel.

### MPR

Purpose currently unknown. (PS3)

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | UInt32[4] | Unknown data|

### MDR

Purpose currently unknown. (PS3)

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | UInt32[4] | Unknown data|

### ENVD

This chunk defines which vertices are affected by a given bone (referenced by its name) and by how much (weight). It is redundant since this info is already given by the STMS buffer, however the game uses the ENVD order as a bone map. 

For example if the first ENVD of a MESH chunk container references the bone "larm", then a 0 bone index in the STMS buffer will refer to "larm", whereas the 0 index in the skeleton would normally refer to the bone "trans". Therefore, when combined together, the ENVD chunks form a bone map, defining a skeleton subset that deforms the submesh.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x2 | UInt16 | Bone name offset (relative to the end of the chunk header)|
| 0x12 | 0x2 | UInt16 | Vertex indices count |
| 0x14 | 0x4 | UInt32 | Vertex indices offset (relative to the end of the chunk header)|
| 0x18 | 0x2 | UInt16 | Weights offset (relative to the end of the chunk header)|
| 0x1A | 0x2 | UInt16 | Weight count (should match the vertex count) |
| 0x12 | 0x2 | UInt16 | Vertex indices offset duplicate|
| 0x14 | 0x2 | UInt16 | Weights offset duplicate|
| 0x16 | 0x2 | UInt16 | Padding|
| Bone name offset | Variable | String | Bone name |
| Vertex indices offset | Vertex indices count x 0x2 | UInt16[Vertex indices count] | The indices of the vertices deformed by the bone |
| Weights offset | Weight count | UByte[Weight count] | The weight influence of the bone on the vertex, as a normalized UByte (value/255) |

### RSID

Resource ID?  References a resource located in another file.  Typically seen in the environment files referencing a shader.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | String | Resource Name|

### RSTP

Resource Type?  Type of resource identified in RSID.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | String | Resource Type (e.g. sdrb)|

### PRID

Source location of remote resource

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | String | Source File|

### PRTP

File type (or extension) of remote resource

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | String | File Extension (e.g. trb)|

### AABB / COMP

This chunk contains some bounding box info.  AABB chunks are used for identifying viewable meshes in-game while
COMP chunks use some bounding box like information used to determine the scale/bias, which is then used to
dequantize the submeshes' position data.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0xC | Float32[3] | Bounding box minimum coordinates|
| 0x1C | 0xC | Float32[3] | Bounding box maximum coordinates|
| 0x28 | 0x8 | UInt32[2] | Reserved, always null ? |

The dequantization is done in the vertex shader, using the following routine :
```
scale = BBoxMax - BBoxMin;
scale *= 0.5;
bias = BBoxMax - posScale;
position = position/32767 * scale + bias
```
### PESH

Purpose currently unknown.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x28 | Float32[10] | Unknown data|
| 0x38 | 0x10 | Char[16] | Not always alpha-numeric, sometimes has a <SOH> 1st character |
| 0x48 | 0x8 | Float32[2] | Unknown data|

### LTCD Header

Always empty so probably unused by the game.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x10 | UInt32[4] | Reserved, always null.|

### MINS Header

Purpose currently unknown.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x04 | Int32 | Associated Skeleton Joint Index/Hash |
| 0x14 | 0x04 | UInt32 | Associated MDL # |
| 0x18 | 0x28 | UInt32[10] | Unknown data|

--------------------------------

## Chunk Containers

### Chunk Container Header

The following header is for all the different chunks.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x10 | [Chunk Header](https://lr-research-team.github.io/wiki/trb/#chunk-header) | Chunk Header |
| 0x10 | 0x4 | UInt32 | Children chunk count |
| 0x14 | 0xC | UInt32[3]| Reserved, always null.|

### SHD

This is the main chunk container for the shader section.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | Variable | [FILE[Count depending on the game]](https://lr-research-team.github.io/wiki/trb/#FILE) | FILE Chunks |
| Variable | 0x20 | [VCAP](https://lr-research-team.github.io/wiki/trb/#VCAP) | VCAP Chunk |
| Variable | 0x90 | [PCAP](https://lr-research-team.github.io/wiki/trb/#PCAP) | PCAP Chunk |
| Variable | Variable | [PRAM](https://lr-research-team.github.io/wiki/trb/#PRAM) | PRAM Chunk |

### WRB

This is the main chunk container for the geometry section. Its underlying chunk containers are all in Big Endian.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | Variable | [MDLC](https://lr-research-team.github.io/wiki/trb/#MDLC) | MDLC Chunk Container |
| Variable | 0x40 | [LTCD](https://lr-research-team.github.io/wiki/trb/#LTCD) | LTCD Chunk Container |
| Variable | Variable | [MICT](https://lr-research-team.github.io/wiki/trb/#MICT) | MICT Chunk Container |
| Variable | 0x70 | [PESR](https://lr-research-team.github.io/wiki/trb/#PESR) | PESR Chunk Container (not always present)|

### MDLC

This chunk container has the "main" model geometry information embedded. It's the biggest one of the 3 containers defined in the SEDBwrb section.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x30 | [MDLC Header Chunk](https://lr-research-team.github.io/wiki/trb/#mdlc-header) | MDLC Header Chunk |
| 0x50 | Variable | [MDL Chunk](https://lr-research-team.github.io/wiki/trb/#MDL)[Variable count] | MDL Chunk Containers (count given in the MDLC Header chunk)|

### MDL

This chunk container defines a mesh and its underlying submeshes, defined in "MESH" chunks.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | Variable | [Name Chunk](https://lr-research-team.github.io/wiki/trb/#name) | The MDL name |
| Variable | 0x30 | [MDL Header Chunk](https://lr-research-team.github.io/wiki/trb/#mdl-header) | MDL Header Chunk |
| Variable | Variable | [MESH Chunk](https://lr-research-team.github.io/wiki/trb/#MESH)[Variable count] | MESH Chunk Containers (count given in the MDLC Header chunk)|
| Variable | 0x80 | [AABB Chunk Container](https://lr-research-team.github.io/wiki/trb/#AABB-container) | The MDL's bounding box and scale/bias info |

### MESH

This chunk container defines a submesh. It has the vertex buffers necessary to construct the geometry.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x20 | [MESH Header Chunk](https://lr-research-team.github.io/wiki/trb/#MESH-header) | MESH Header Chunk |
| 0x40 | Variable | [STR Chunk](https://lr-research-team.github.io/wiki/trb/#str) | This chunk defines the shader used for this submesh, giving its name.|
| Variable | 0x20 | [RSID Chunk](https://lr-research-team.github.io/wiki/trb/#rsid) | External resource name info |
| Variable | 0x20 | [RSTP Chunk](https://lr-research-team.github.io/wiki/trb/#rstp) | External resource type info |
| Variable | 0x20 | [PRID Chunk](https://lr-research-team.github.io/wiki/trb/#prid) | External resource source file location info |
| Variable | 0x20 | [PRTP Chunk](https://lr-research-team.github.io/wiki/trb/#prtp) | External resource file type info |
| Variable | Variable | [STMS](https://lr-research-team.github.io/wiki/trb/#STMS)[Variable count] | STMS Chunks (count given in the MESH Header chunk)|
| Variable | 0x20 | [MPR](https://lr-research-team.github.io/wiki/trb/#MPR)[Variable count] | MPR Chunks (not always present, count given in the MESH Header chunk)|
| Variable | 0x20 | [MDR](https://lr-research-team.github.io/wiki/trb/#MDR)[Variable count] | MDR Chunks (not always present, count given in the MESH Header chunk)|
| Variable | Variable | [ENVD](https://lr-research-team.github.io/wiki/trb/#ENVD)[Variable count] | ENVD Chunks (count given in the MESH Header chunk)|
| Variable | 0x50 | [AABB Chunk Container](https://lr-research-team.github.io/wiki/trb/#AABB-container) | The mesh's bounding box info |

### AABB Container

This chunk container is used to define bounding box information (Mesh & MDL) and scale/bias information (MDL only).

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x30 | [AABB Chunk](https://lr-research-team.github.io/wiki/trb/#AABB-/-Comp)[Variable count] | AABB Chunk |

### LTCD

This chunk container only has a header chunk. Its purpose is currently unknown, considering its size it's probably unused.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x10 | [LTCD Header Chunk](https://lr-research-team.github.io/wiki/trb/#ltcd-header) | LTCD Header Chunk |

### MICT

This chunk container only has a single embedded chunk container. Its purpose is currently unknown.

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | Variable | [MINS Chunk](https://lr-research-team.github.io/wiki/trb/#MINS)[Variable count] | MINS Chunk Containers, which count is always equal to the number of MDL in the MDLC Chunk Container.|

### MINS

Purpose currently unknown

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x40 | [MINS Header Chunk](https://lr-research-team.github.io/wiki/trb/#mins-header) | MINS Header Chunk |
| 0x60 | Variable | [NAME Chunk](https://lr-research-team.github.io/wiki/trb/#mins-name) | Associated Skeleton Joint Name |

### PESR

Purpose currently unknown

| Offset | Size | Type | Description |
| --- | --- | --- | --- |
| 0x0 | 0x20 | [Chunk Container Header](https://lr-research-team.github.io/wiki/trb/#chunk-container-header) | Chunk Container Header |
| 0x20 | 0x50 | [PESH Chunk](https://lr-research-team.github.io/wiki/trb/#PESH)[Variable count] | PESH Chunk |

--------------------------------