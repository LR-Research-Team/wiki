The field names in the WDB files indicates how to parse each record's binary data and is present only in XIII-2 and XIII-LR's WDB files. each field would begin with a single letter that indicates the type of field, a number that indicates the amount of bits used by that field's value, and a small description about what the field is supposed to do ingame. 

## Field name types

The following list contains commonly used starting letters for the field names.

| Field Letter | Description |
| -- | -- |
| f | represents a floating point value field |
| f# | represents a non decimal signed integer value field |
| i# | represents a signed integer value field |
| s | represents a string value field |
| s# | represents a string value field. the value points to the string item's index in the !!strArray section |
| u# | represents an unsigned integer value field |

# Field names for FINAL FANTASY XIII's WDBs
This section contains manually reversed field names for each WDB file from FINAL FANTASY XIII. as of now the field names are reversed and given only for some of the WDB files. more will be added to this page slowly when their field names are reversed.

<br>All the offsets values are in Big Endian order. 

## auto_clip.wdb
| Field | Type | Description |
| -- | -- | -- |
| sTitle | UInt32 | relative offset in !!string section |
| sTarget | UInt32 | relative offset in !!string section |
| sTarget2 | UInt32 | relative offset in !!string section |
| sText | UInt32 | relative offset in !!string section |
| sPicture | UInt32 | relative offset in !!string section |
| u4Category | Bits | Unsigned 4 bits |
| u7Sort | Bits | Unsigned 7 bits |
| u4Chapter | Bits | Unsigned 4 bits |

## bt_chainbonus.wdb
| Field | Type | Description |
| -- | -- | -- |
| u6WhoFrom | Bits | Unsigned 6 bits |
| u6When0 | Bits | Unsigned 6 bits |
| u6When1 | Bits | Unsigned 6 bits |
| u6When2 | Bits | Unsigned 6 bits |
| u6WhatState | Bits | Unsigned 6 bits |
| u6WhoTo | Bits | Unsigned 6 bits |
| u6DoWhat | Bits | Unsigned 6 bits |
| u6Where | Bits | Unsigned 6 bits |
| u6How | Bits | Unsigned 6 bits |
| u16Bonus | Bits | Unsigned 16 bits |

## bt_chara_prop.wdb
| Field | Type | Description |
| -- | -- | -- |
| sInfoStrId | UInt32 | relative offset in !!string section |
| sOpenCondArgS0 | UInt32 | relative offset in !!string section |
| u1NoLibra | Bits | Unsigned 1 bit |
| u8OpenCond | Bits | Unsigned 8 bits |
| u8AiOrderEn | Bits | Unsigned 8 bits |
| u8AiOrderJm | Bits | Unsigned 8 bits |
| u4FlavorAtk | Bits | Unsigned 4 bits |
| u4FlavorBla | Bits | Unsigned 4 bits |
| u4FlavorDef | Bits | Unsigned 4 bits |

## bt_constants.wdb
| Field | Type | Description |
| -- | -- | -- |
| iiVal | Int32 | int32 value |
| ffVal | Float32 | float value |
| ssVal | UInt32 | relative offset in !!string section |

## item.wdb
| Field | Type | Description |
| -- | -- | -- |
| sItemNameStringId | UInt32 | relative offset in !!string section |
| sHelpStringId | UInt32 | relative offset in !!string section |
| sScriptId | UInt32 | relative offset in !!string section |
| uPurchasePrice | UInt32 | uint32 value |
| uSellPrice | UInt32 | uint32 value |
| u8MenuIcon | Bits | Unsigned 8 bits |
| u8ItemCategory | Bits | Unsigned 8 bits |
| i16ScriptArg0 | Bits | Signed 16 bits | 
| i16ScriptArg1 | Bits | Signed 16 bits | 
| u1IsUseBattleMenu | Bits | Unsigned 1 bit |
| u1IsUseMenu | Bits | Unsigned 1 bit |
| u1IsDisposable | Bits | Unsigned 1 bit |
| u1IsSellable | Bits | Unsigned 1 bit |
| u5Rank | Bits | Unsigned 5 bits |
| u6Genre | Bits | Unsigned 6 bits |
| u1IsIgnoreGenre | Bits | Unsigned 1 bit |
| u16SortAllByKCategory | Bits | Unsigned 16 bits |
| u16SortCategoryByCategory | Bits | Unsigned 16 bits |
| u16Experience | Bits | Unsigned 16 bits |
| i16Mulitplier | Bits | Signed 16 bits |
| u1IsUseItemChange | Bits | Unsigned 1 bit |

## item_consume.wdb
| Field | Type | Description |
| -- | -- | -- |
| sAbilityId | UInt32 | relative offset in !!string section |
| sLearnAbilityId | UInt32 | relative offset in !!string section |
| u1IsUseRemodel | Bits | Unsigned 1 bit |
| u1IsUseGrow | Bits | Unsigned 1 bit |
| u16ConsumeAP | Bits | Unsigned 16 bits |

## item_weapon.wdb

N.B: Only reversed partially

| Field | Type | Description |
| -- | -- | -- |
| sWeaponCharaSpecId | UInt32 | relative offset in !!string section |
| sWeaponCharaSpecId2 | UInt32 | relative offset in !!string section |
| sAbility | UInt32 | relative offset in !!string section |
| sAbility2 | UInt32 | relative offset in !!string section |
| sAbility3 | UInt32 | relative offset in !!string section |
| sUpgradeAbility | UInt32 | relative offset in !!string section |
| sAbilityHelpStringId | UInt32 | relative offset in !!string section |
| uBuyPriceIncrement | UInt32 | uint32 value |
| uSellPriceIncrement | UInt32 | uint32 value |
| sDisasItem1 | UInt32 | relative offset in !!string section |
| sDisasItem2 | UInt32 | relative offset in !!string section |
| sDisasItem3 | UInt32 | relative offset in !!string section |
| sDisasItem4 | UInt32 | relative offset in !!string section |
| sDisasItem5 | UInt32 | relative offset in !!string section |
| u8UnkVal1 | Bits | Unsigned 8 bits |
| u8UnkVal2 | Bits | Unsigned 8 bits |
| u2UnkVal3 | Bits | Unsigned 2 bits |
| u7MaxLvl | Bits | Unsigned 7 bits |
| u4UnkVal4 | Bits | Unsigned 4 bits |
| u1UnkBool1 | Bits | Unsigned 1 bit |
| u1UnkBool2 | Bits | Unsigned 1 bit |
| u1UnkBool3 | Bits | Unsigned 1 bit |
| i10ExpRate1 | Bits | Signed 10 bits |
| i10ExpRate2 | Bits | Signed 10 bits |
| i10ExpRate3 | Bits | Signed 10 bits |
| u1UnkBool4 | Bits | Unsigned 1 bit |
| u1UnkBool5 | Bits | Unsigned 1 bit |
| u8StatusModKind0 | Bits | Unsigned 8 bits |
| u8StatusModKind1 | Bits | Unsigned 8 bits |
| u4StatusModType | Bits | Unsigned 4 bits |
| u1UnkBool6 | Bits | Unsigned 1 bit |
| u1UnkBool7 | Bits | Unsigned 1 bit |
| u16UnkVal5 | Bits | Unsigned 16 bits |
| i16StatusModVal | Bits | Signed 16 bits |
| u16UnkVal6 | Bits | Unsigned 16 bits |
| i16AttackModVal | Bits | Signed 16 bits |
| u16UnkVal7 | Bits | Unsigned 16 bits |
| i16MagicModVal | Bits | Signed 16 bits |
| i16AtbModVal | Bits | Signed 16 bits |
| u16UnkVal8 | Bits | Unsigned 16 bits |
| u16UnkVal9 | Bits | Unsigned 16 bits |
| u16UnkVal10 | Bits | Unsigned 16 bits |
| u14DisasRate1 | Bits | Unsigned 14 bits |
| u7UnkVal11 | Bits | Unsigned 7 bits |
| u7UnkVal12 | Bits | Unsigned 7 bits |
| u14DisasRate2 | Bits | Unsigned 14 bits |
| u14DisasRate3 | Bits | Unsigned 14 bits |
| u7UnkVal13 | Bits | Unsigned 7 bits |
| u14DisasRate4 | Bits | Unsigned 14 bits |
| u7UnkVal14 | Bits | Unsigned 7 bits |
| u14DisasRate5 | Bits | Unsigned 14 bits |

## monster_book.wdb
| Field | Type | Description |
| -- | -- | -- |
| u6MbookId | Bits | Unsigned 6 bits |
| u9SortId | Bits | Unsigned 9 bits |
| u9PictureId | Bits | Unsigned 9 bits |
| u1Unk | Bits | Unsigned 1 bit |

## movie_items.win32.wdb

N.B: also applies to movie_items.win32_us.wdb file

| Field | Type | Description |
| -- | -- | -- |
| sZoneName | UInt32 | relative offset in !!string section |
| uCinemaSize | UInt32 | uint32 value |
| uReserved | UInt32 | uint32 value |
| uCinemaStart | UInt32 | uint32 value |

The ps3 version of this file uses the uReserved and uCinemaStart fields together as an UInt64 value.

## party.wdb
| Field | Type | Description |
| -- | -- | -- |
| sCharaSpecId | UInt32 | relative offset in !!string section |
| sSubCharaSpecId0 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId1 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId2 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId3 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId4 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId5 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId6 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId7 | UInt32 | relative offset in !!string section |
| sSubCharaSpecId8 | UInt32 | relative offset in !!string section |
| sRideObjectCharaSpecId0 | UInt32 | relative offset in !!string section |
| sRideObjectCharaSpecId1 | UInt32 | relative offset in !!string section |
| sFieldFreeCameraSettingResourceId | UInt32 | relative offset in !!string section |
| sIconResourceId | UInt32 | relative offset in !!string section |
| sScriptIdOnPartyCharaAIStarted | UInt32 | relative offset in !!string section |
| sScriptIdOnIdle | UInt32 | relative offset in !!string section |
| sBattleCharaSpecId | UInt32 | relative offset in !!string section |
| sSummonId | UInt32 | relative offset in !!string section |
| fStopDistance | Float32 | float value |
| fWalkDistance | Float32 | float value |
| fPlayerRestraint | Float32 | float value |
| u1IsEnableUserControl | Bits | Unsigned 1 bit |
| u5OrderNumForCrest | Bits | Unsigned 5 bits |
| u8OrderNumForTool | Bits | Unsigned 8 bits |
| u7Expresspower | Bits | Unsigned 7 bits |
| u7Willpower | Bits | Unsigned 7 bits |
| u7Brightness | Bits | Unsigned 7 bits |
| u7Cognition | Bits | Unsigned 7 bits |

## savepoint.wdb
| Field | Type | Description |
| -- | -- | -- |
| sLoadScriptId | UInt32 | relative offset in !!string section |
| i17PartyPositionMarkerGroupIndex | Bits | Signed 17 bits | 
| u15SaveIconBackgroundImageIndex | Bits | Unsigned 15 bits |
| i16SaveIconOverrideImageIndex | Bits | Signed 16 bits |

## sound_fileid_dic.wdb

N.B: also applies to sound_fileid_dic_us.wdb file

| Field | Type | Description |
| -- | -- | -- |
| i31FileId | Bits | Signed 31 bits |
| u1IsStream | Bits | Unsigned 1 bit |

## sound_filename_dic.wdb

N.B: also applies to sound_filename_dic_us.wdb

| Field | Type | Description |
| -- | -- | -- |
| sResourceName | UInt32 | relative offset in !!string section |

## special_ability.wdb
| Field | Type | Description |
| -- | -- | -- |
| sAbility | UInt32 | relative offset in !!string section |
| u6Genre | Bits | Unsigned 6 bits |
| u3Count | Bits | Unsigned 3 bits |

## treasurebox.wdb
| Field | Type | Description |
| -- | -- | -- |
| sItemResourceId | UInt32 | relative offset in !!string section |
| iItemCount | Int32 | int32 value |
| sNextTreasureBoxResourceId | UInt32 | relative offset in !!string section |

## white.wdb
| Field | Type | Description |
| -- | -- | -- |
| fVal | Float32 | float value |
| iVal1 | Int32 | int32 value |
| sResourceName | UInt32 | relative offset in !!string section |
| fPosX | Float32 | float value |
| fPosY | Float32 | float value |
| fPosZ | Float32 | float value |

## zonelist.wdb
| Field | Type | Description |
| -- | -- | -- |
| fMovieTotalTimeSec | Float32 | float value |
| iImageSize | Int32 | int32 value |
| u8RefZoneNum0 | Bits | Unsigned 8 bits |
| u8RefZoneNum1 | Bits | Unsigned 8 bits |
| u8RefZoneNum2 | Bits | Unsigned 8 bits |
| u8RefZoneNum3 | Bits | Unsigned 8 bits |
| u8RefZoneNum4 | Bits | Unsigned 8 bits |
| u8RefZoneNum5 | Bits | Unsigned 8 bits |
| u8RefZoneNum6 | Bits | Unsigned 8 bits |
| u8RefZoneNum7 | Bits | Unsigned 8 bits |
| u8RefZoneNum8 | Bits | Unsigned 8 bits |
| u8RefZoneNum9 | Bits | Unsigned 8 bits |
| u8RefZoneNum10 | Bits | Unsigned 8 bits |
| u1OnDisk0 | Bits | Unsigned 1 bit |
| u1OnDisk1 | Bits | Unsigned 1 bit |
| u1OnDisk2 | Bits | Unsigned 1 bit |
| u1OnDisk3 | Bits | Unsigned 1 bit |
| u1On1stLayerPS3 | Bits | Unsigned 1 bit |
| u1On2ndtLayerPS3 | Bits | Unsigned 1 bit |

## z###.wdb

N.B: applies to the wdb files present inside each zone\z### folders

| Field | Type | Description |
| -- | -- | -- |
| iBaseNum | Int32 | int32 value |
| sName0 | UInt32 | relative offset in !!string section |
| sName1 | UInt32 | relative offset in !!string section |