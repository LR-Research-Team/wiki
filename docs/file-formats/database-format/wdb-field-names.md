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
This section contains manually reversed field names for each WDB file from FINAL FANTASY XIII. as of now the field names are given only for some of the WDB files and more will be added to this page slowly when their field names are identified. do know that some of them may not be correct and if you encounter such incorrect fields, please report them in the Fabula Nova Chrystalis discord server.

<br>All the offsets values are stored in Big Endian order. for non 32bit type fields, the fields would have to be applied from a right to left order on a 4byte set of a record's data. if you run out of bits in that 4bytes set, then apply the fields to the next 4bytes set, in the same right to left order.

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

## actioneffect.wdb
| Field | Type | Description |
| -- | -- | -- |
| sEffectId | UInt32 | relative offset in !!string section |
| iEffectArg1 | Int32 | int32 value |
| sSoundId | UInt32 | relative offset in !!string section |

## attreffect.wdb
| Field | Type | Description |
| -- | -- | -- |
| sFootSoundResourceNameDefaultAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameDrySoilAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameDampSoilAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameGrassAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameBushAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameSandAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameWoodAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameBoardAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameFlooringAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameStoneAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameGravelAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameIronAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameThinIronAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameClothAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameEartenwareAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameCrystalAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameGlassAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameIceAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameWaterAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameAsphaltAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameNoneAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameWireNetAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameBranchOfMachineAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameBranchOfNatureAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameCorkAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameMarbleAttr | UInt32 | relative offset in !!string section |
| sFootSoundResourceNameHologramAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameDefaultAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameDrySoilAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameDampSoilAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameGrassAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameBushAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameSandAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameWoodAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameBoardAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameFlooringAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameStoneAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameGravelAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameIronAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameThinIronAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameClothAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameEartenwareAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameCrystalAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameGlassAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameIceAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameWaterAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameAsphaltAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameNoneAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameWireNetAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameBranchOfMachineAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameBranchOfNatureAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameCorkAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameMarbleAttr | UInt32 | relative offset in !!string section |
| sFootVfxResourceNameHologramAttr | UInt32 | relative offset in !!string section |

## attreffectstate.wdb
| Field | Type | Description |
| -- | -- | -- |
| sWalk | UInt32 | relative offset in !!string section |
| sRun | UInt32 | relative offset in !!string section |
| sJump | UInt32 | relative offset in !!string section |
| sRetreat | UInt32 | relative offset in !!string section |
| sLanding | UInt32 | relative offset in !!string section |
| sSliding | UInt32 | relative offset in !!string section |
| sSquat | UInt32 | relative offset in !!string section |
| sStand | UInt32 | relative offset in !!string section |
| sFly | UInt32 | relative offset in !!string section |

## bt_ability.wdb
| Field | Type | Description |
| -- | -- | -- |
| sStringResId | UInt32 | relative offset in !!string section |
| sInfoStResId | UInt32 | relative offset in !!string section |
| sScriptId | UInt32 | relative offset in !!string section |
| sAblArgStr0 | UInt32 | relative offset in !!string section |
| sAblArgStr1 | UInt32 | relative offset in !!string section |
| sAutoAblStEff0 | UInt32 | relative offset in !!string section |
| fDistanceMin | Float32 | float value |
| fDistanceMax | Float32 | float value |
| fMaxJumpHeight | Float32 | float value |
| fYDistanceMin | Float32 | float value |
| fYDistanceMax | Float32 | float value |
| fAirJpHeight | Float32 | float value |
| fAirJpTime | Float32 | float value |
| sReplaceAirAttack | UInt32 | relative offset in !!string section |
| sReplaceAirAir | UInt32 | relative offset in !!string section |
| sReplaceRangeAtk | UInt32 | relative offset in !!string section |
| sReplaceFinAtk | UInt32 | relative offset in !!string section |
| sReplaceEnAttr | UInt32 | relative offset in !!string section |
| iExceptionID | Int32 | int32 value |
| sActionId0 | UInt32 | relative offset in !!string section |
| sActionId1 | UInt32 | relative offset in !!string section |
| sActionId2 | UInt32 | relative offset in !!string section |
| sActionId3 | UInt32 | relative offset in !!string section |
| sRtDamSrc | UInt32 | relative offset in !!string section |
| sRefDamSrc | UInt32 | relative offset in !!string section |
| sSubRefDamSrc | UInt32 | relative offset in !!string section |
| sSlamDamSrc | UInt32 | relative offset in !!string section |
| sCamArtsSeqId0 | UInt32 | relative offset in !!string section |
| sCamArtsSeqId1 | UInt32 | relative offset in !!string section |
| sCamArtsSeqId2 | UInt32 | relative offset in !!string section |
| sCamArtsSeqId3 | UInt32 | relative offset in !!string section |
| sRedirectAbility0 | UInt32 | relative offset in !!string section |
| sRedirectTo0 | UInt32 | relative offset in !!string section |
| sRedirectAbility1 | UInt32 | relative offset in !!string section |
| sRedirectTo1 | UInt32 | relative offset in !!string section |
| sRedirectAbility2 | UInt32 | relative offset in !!string section |
| sRedirectTo2 | UInt32 | relative offset in !!string section |
| sRedirectAbility3 | UInt32 | relative offset in !!string section |
| sRedirectTo3 | UInt32 | relative offset in !!string section |
| sSysEffId0 | UInt32 | relative offset in !!string section |
| iSysEffArg0 | Int32 | int32 value |
| sSysSndId0 | UInt32 | relative offset in !!string section |
| sRtEffId0 | UInt32 | relative offset in !!string section |
| iRtEffArg0 | Int32 | int32 value |
| sRtSndId0 | UInt32 | relative offset in !!string section |
| sRtEffId1 | UInt32 | relative offset in !!string section |
| iRtEffArg1 | Int32 | int32 value |
| sRtSndId1 | UInt32 | relative offset in !!string section |
| sRtEffId2 | UInt32 | relative offset in !!string section |
| iRtEffArg2 | Int32 | int32 value |
| sRtSndId2 | UInt32 | relative offset in !!string section |
| sRtEffId3 | UInt32 | relative offset in !!string section |
| iRtEffArg3 | Int32 | int32 value |
| sRtSndId3 | UInt32 | relative offset in !!string section |
| sRtEffId4 | UInt32 | relative offset in !!string section |
| iRtEffArg4 | Int32 | int32 value |
| sRtSndId4 | UInt32 | relative offset in !!string section |
| u1ComAbility | Bits | Unsigned 1 bit |
| u1RsvFlag0 | Bits | Unsigned 1 bit |
| u1RsvFlag1 | Bits | Unsigned 1 bit |
| u1RsvFlag2 | Bits | Unsigned 1 bit |
| u1RsvFlag3 | Bits | Unsigned 1 bit |
| u1RsvFlag4 | Bits | Unsigned 1 bit |
| u1RsvFlag5 | Bits | Unsigned 1 bit |
| u1RsvFlag6 | Bits | Unsigned 1 bit |
| u4ArtsNameHideKd | Bits | Unsigned 4 bits |
| u16ArtsNameFrame | Bits | Unsigned 16 bits |
| u4UseRole | Bits | Unsigned 4 bits |
| u8AblSndKind | Bits | Unsigned 8 bits |
| u4MenuCategory | Bits | Unsigned 4 bits |
| i16MenuSortNo | Bits | Signed 16 bits |
| u1NoDespel | Bits | Unsigned 1 bit |
| i16ScriptArg0 | Bits | Signed 16 bits |
| i16ScriptArg1 | Bits | Signed 16 bits |
| u8AbilityKind | Bits | Unsigned 8 bits |
| u4TargetListKind | Bits | Unsigned 4 bits |
| i16AblArgInt0 | Bits | Signed 16 bits |
| u4UpAblKind | Bits | Unsigned 4 bits |
| i16AblArgInt1 | Bits | Signed 16 bits |
| i16AtbCount | Bits | Signed 16 bits |
| i16AtRnd | Bits | Signed 16 bits |
| i16KeepVal | Bits | Signed 16 bits |
| i16IntRsv0 | Bits | Signed 16 bits |
| i16IntRsv1 | Bits | Signed 16 bits |
| u1TgFoge | Bits | Unsigned 1 bit |
| u1NoBackStep | Bits | Unsigned 1 bit |
| u1AIWanderFlag | Bits | Unsigned 1 bit |
| u16TgElemId | Bits | Unsigned 16 bits |
| u10OpProp0 | Bits | Unsigned 10 bits |
| u1AutoAblStEfEd0 | Bits | Unsigned 1 bit |
| u1CheckAutoRpl | Bits | Unsigned 1 bit |
| u1SeqParts | Bits | Unsigned 1 bit |
| i16AutoAblStEfTi0 | Bits | Signed 16 bits |
| u4YRgCheckType | Bits | Unsigned 4 bits |
| u4AtDistKind | Bits | Unsigned 4 bits |
| u4JumpAttackType | Bits | Unsigned 4 bits |
| u1SeqTermination | Bits | Unsigned 1 bit |
| u5ActSelType | Bits | Unsigned 5 bits |
| u4LoopFinCond | Bits | Unsigned 4 bits |
| u16LoopFinArg	| Bits | Unsigned 16 bits |
| u4RedirectMargeNof0 | Bits | Unsigned 4 bits |
| i16RefDamSrcRpt | Bits | Signed 16 bits |
| i16SubRefDamSrcRp | Bits | Signed 16 bits |
| i8AreaRad | Bits | Signed 8 bits |
| u8CamArtsSelType | Bits | Unsigned 8 bits |
| u4RedirectMargeNof1 | Bits | Unsigned 4 bits |
| u4RedirectMargeNof2 | Bits | Unsigned 4 bits |
| u4RedirectMargeNof3 | Bits | Unsigned 4 bits |
| u16SysEffPos0 | Bits | Unsigned 16 bits |
| u16RtEffPos0 | Bits | Unsigned 16 bits |
| u16RtEffPos1 | Bits | Unsigned 16 bits |
| u16RtEffPos2	| Bits | Unsigned 16 bits |
| u16RtEffPos3 | Bits | Unsigned 16 bits |
| u16RtEffPos4 | Bits | Unsigned 16 bits |

## bt_auto_ability.wdb
| Field | Type | Description |
| -- | -- | -- |
| sStringResId | UInt32 | relative offset in !!string section |
| sInfoStResId | UInt32 | relative offset in !!string section |
| sScriptId | UInt32 | relative offset in !!string section |
| sAutoAblArgStr0 | UInt32 | relative offset in !!string section |
| sAutoAblArgStr1 | UInt32 | relative offset in !!string section |
| u1RsvFlag0 | Bits | Unsigned 1 bit |
| u1RsvFlag1 | Bits | Unsigned 1 bit |
| u1RsvFlag2 | Bits | Unsigned 1 bit |
| u1RsvFlag3 | Bits | Unsigned 1 bit |
| u4UseRole | Bits | Unsigned 4 bits |
| u4MenuCategory | Bits | Unsigned 4 bits |
| i16MenuSortNo | Bits | Signed 16 bits |
| i16ScriptArg0 | Bits | Signed 16 bits |
| i16ScriptArg1 | Bits | Signed 16 bits |
| u8AutoAblKind | Bits | Unsigned 8 bits |
| i16AutoAblArgInt0 | Bits | Signed 16 bits |
| i16AutoAblArgInt1 | Bits | Signed 16 bits |
| i16WepLvArg0 | Bits | Signed 16 bits |
| i16WepLvArg1 | Bits | Signed 16 bits |

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

## bt_summon.wdb
| Field | Type | Description |
| -- | -- | -- |
| iSummonKind | Int32 | int32 value |
| sCharaSet | UInt32 | relative offset in !!string section |
| sCharaSet | UInt32 | relative offset in !!string section |
| sBtChSpec0 | UInt32 | relative offset in !!string section |
| sBtChSpec1 | UInt32 | relative offset in !!string section |
| sSummonInEv | UInt32 | relative offset in !!string section |
| sDriveInEv | UInt32 | relative offset in !!string section |
| sFinishArtsEv | UInt32 | relative offset in !!string section |
| iMaxSp0 | Int32 | int32 value |
| iMaxSp1 | Int32 | int32 value |
| iMaxSp2 | Int32 | int32 value |
| iMaxSp3 | Int32 | int32 value |
| iMaxSp4 | Int32 | int32 value |
| iMaxSp5 | Int32 | int32 value |
| iMaxSp6 | Int32 | int32 value |
| iMaxSp7 | Int32 | int32 value |
| iMaxSp8 | Int32 | int32 value |
| iMaxSp9 | Int32 | int32 value |
| iMaxSp10 | Int32 | int32 value |
| iMaxSp11 | Int32 | int32 value |
| iMaxSp12 | Int32 | int32 value |
| iMaxSp13 | Int32 | int32 value |
| iMaxSp14 | Int32 | int32 value |
| iMaxSp15 | Int32 | int32 value |
| iMaxSp16 | Int32 | int32 value |
| u16Str0 | Bits | Unsigned 16 bits |
| u16Str1 | Bits | Unsigned 16 bits |
| u16Str2 | Bits | Unsigned 16 bits |
| u16Str3 | Bits | Unsigned 16 bits |
| u16Str4 | Bits | Unsigned 16 bits |
| u16Str5 | Bits | Unsigned 16 bits |
| u16Str6 | Bits | Unsigned 16 bits |
| u16Str7 | Bits | Unsigned 16 bits |
| u16Str8 | Bits | Unsigned 16 bits |
| u16Str9 | Bits | Unsigned 16 bits |
| u16Str10 | Bits | Unsigned 16 bits |
| u16Str11 | Bits | Unsigned 16 bits |
| u16Str12 | Bits | Unsigned 16 bits |
| u16Str13 | Bits | Unsigned 16 bits |
| u16Str14 | Bits | Unsigned 16 bits |
| u16Str15 | Bits | Unsigned 16 bits |
| u16Str16 | Bits | Unsigned 16 bits |
| u16Mag0 | Bits | Unsigned 16 bits |
| u16Mag1 | Bits | Unsigned 16 bits |
| u16Mag2 | Bits | Unsigned 16 bits |
| u16Mag3 | Bits | Unsigned 16 bits |
| u16Mag4 | Bits | Unsigned 16 bits |
| u16Mag5 | Bits | Unsigned 16 bits |
| u16Mag6 | Bits | Unsigned 16 bits |
| u16Mag7 | Bits | Unsigned 16 bits |
| u16Mag8 | Bits | Unsigned 16 bits |
| u16Mag9 | Bits | Unsigned 16 bits |
| u16Mag10 | Bits | Unsigned 16 bits |
| u16Mag11 | Bits | Unsigned 16 bits |
| u16Mag12 | Bits | Unsigned 16 bits |
| u16Mag13 | Bits | Unsigned 16 bits |
| u16Mag14 | Bits | Unsigned 16 bits |
| u16Mag15 | Bits | Unsigned 16 bits |
| u16Mag16 | Bits | Unsigned 16 bits |

## charaset.wdb
| Field | Type | Description |
| -- | -- | -- |
| iMemorySizeLimit | Int32 | int32 value |
| iVideoMemorySizeLimit | Int32 | int32 value |
| sCharaSpecId0 | UInt32 | relative offset in !!string section |
| sCharaSpecId1 | UInt32 | relative offset in !!string section |
| sCharaSpecId2 | UInt32 | relative offset in !!string section |
| sCharaSpecId3 | UInt32 | relative offset in !!string section |
| sCharaSpecId4 | UInt32 | relative offset in !!string section |
| sCharaSpecId5 | UInt32 | relative offset in !!string section |
| sCharaSpecId6 | UInt32 | relative offset in !!string section |
| sCharaSpecId7 | UInt32 | relative offset in !!string section |
| sCharaSpecId8 | UInt32 | relative offset in !!string section |
| sCharaSpecId9 | UInt32 | relative offset in !!string section |
| sCharaSpecId10 | UInt32 | relative offset in !!string section |
| sCharaSpecId11 | UInt32 | relative offset in !!string section |
| sCharaSpecId12 | UInt32 | relative offset in !!string section |
| sCharaSpecId13 | UInt32 | relative offset in !!string section |
| sCharaSpecId14 | UInt32 | relative offset in !!string section |
| sCharaSpecId15 | UInt32 | relative offset in !!string section |
| sCharaSpecId16 | UInt32 | relative offset in !!string section |
| sCharaSpecId17 | UInt32 | relative offset in !!string section |
| sCharaSpecId18 | UInt32 | relative offset in !!string section |
| sCharaSpecId19 | UInt32 | relative offset in !!string section |
| sCharaSpecId20 | UInt32 | relative offset in !!string section |
| sCharaSpecId21 | UInt32 | relative offset in !!string section |
| sCharaSpecId22 | UInt32 | relative offset in !!string section |
| sCharaSpecId23 | UInt32 | relative offset in !!string section |
| sCharaSpecId24 | UInt32 | relative offset in !!string section |
| sCharaSpecId25 | UInt32 | relative offset in !!string section |
| sCharaSpecId26 | UInt32 | relative offset in !!string section |
| sCharaSpecId27 | UInt32 | relative offset in !!string section |
| sCharaSpecId28 | UInt32 | relative offset in !!string section |
| sCharaSpecId29 | UInt32 | relative offset in !!string section |
| sCharaSpecId30 | UInt32 | relative offset in !!string section |
| sCharaSpecId31 | UInt32 | relative offset in !!string section |
| sCharaSpecId32 | UInt32 | relative offset in !!string section |
| sCharaSpecId33 | UInt32 | relative offset in !!string section |
| sCharaSpecId34 | UInt32 | relative offset in !!string section |
| sCharaSpecId35 | UInt32 | relative offset in !!string section |
| sCharaSpecId36 | UInt32 | relative offset in !!string section |
| sCharaSpecId37 | UInt32 | relative offset in !!string section |
| sCharaSpecId38 | UInt32 | relative offset in !!string section |
| sCharaSpecId39 | UInt32 | relative offset in !!string section |
| sCharaSpecId40 | UInt32 | relative offset in !!string section |
| sCharaSpecId41 | UInt32 | relative offset in !!string section |
| sCharaSpecId42 | UInt32 | relative offset in !!string section |
| sCharaSpecId43 | UInt32 | relative offset in !!string section |
| sCharaSpecId44 | UInt32 | relative offset in !!string section |
| sCharaSpecId45 | UInt32 | relative offset in !!string section |
| sCharaSpecId46 | UInt32 | relative offset in !!string section |
| sCharaSpecId47 | UInt32 | relative offset in !!string section |
| sCharaSpecId48 | UInt32 | relative offset in !!string section |
| sCharaSpecId49 | UInt32 | relative offset in !!string section |
| sCharaSpecId50 | UInt32 | relative offset in !!string section |
| sCharaSpecId51 | UInt32 | relative offset in !!string section |
| sCharaSpecId52 | UInt32 | relative offset in !!string section |
| sCharaSpecId53 | UInt32 | relative offset in !!string section |
| sCharaSpecId54 | UInt32 | relative offset in !!string section |
| sCharaSpecId55 | UInt32 | relative offset in !!string section |
| sCharaSpecId56 | UInt32 | relative offset in !!string section |
| sCharaSpecId57 | UInt32 | relative offset in !!string section |
| sCharaSpecId58 | UInt32 | relative offset in !!string section |
| sCharaSpecId59 | UInt32 | relative offset in !!string section |
| sCharaSpecId60 | UInt32 | relative offset in !!string section |
| sCharaSpecId61 | UInt32 | relative offset in !!string section |
| sCharaSpecId62 | UInt32 | relative offset in !!string section |
| sCharaSpecId63 | UInt32 | relative offset in !!string section |
| u1PartyLoadRequestIndex0 | Bits | Unsigned 1 bit |
| u1PartyLoadRequestIndex1 | Bits | Unsigned 1 bit |
| u1PartyLoadRequestIndex2 | Bits | Unsigned 1 bit |
| u1PartyLoadRequestIndex3 | Bits | Unsigned 1 bit |
| u1PartyLoadRequestIndex4 | Bits | Unsigned 1 bit |
| u1PartyLoadRequestIndex5 | Bits | Unsigned 1 bit |

## crystal wdb files

* crystal_fang.wdb
* crystal_hope.wdb
* crystal_lightning.wdb
* crystal_sazh.wdb
* crystal_snow.wdb
* crystal_vanille.wdb

| Field | Type | Description |
| -- | -- | -- |
| uCPCost | UInt32 | uint32 value |
| sAbilityID | UInt32 | relative offset in !!string section |
| u4Role | Bits | Unsigned 4 bits |
| u4CrystalStage | Bits | Unsigned 4 bits |
| u8NodeType | Bits | Unsigned 8 bits |
| u16NodeVal | Bits | Unsigned 16 bits |

## emotion_voice.wdb
| Field | Type | Description |
| -- | -- | -- |
| u4RandomMax0 | Bits | Unsigned 4 bits |
| u4RandomMax1 | Bits | Unsigned 4 bits |
| u4RandomMax2 | Bits | Unsigned 4 bits |
| u4RandomMax3 | Bits | Unsigned 4 bits |
| u4RandomMax4 | Bits | Unsigned 4 bits |
| u4RandomMax5 | Bits | Unsigned 4 bits |
| u4RandomMax6 | Bits | Unsigned 4 bits |
| u4RandomMax7 | Bits | Unsigned 4 bits |
| u4RandomMax8 | Bits | Unsigned 4 bits |
| u4RandomMax9 | Bits | Unsigned 4 bits |
| u4AIRandomMax0 | Bits | Unsigned 4 bits |
| u4AIRandomMax1 | Bits | Unsigned 4 bits |
| u4AIRandomMax2 | Bits | Unsigned 4 bits |
| u4AIRandomMax3 | Bits | Unsigned 4 bits |
| u4AIRandomMax4 | Bits | Unsigned 4 bits |
| u4AIRandomMax5 | Bits | Unsigned 4 bits |
| u4AIRandomMax6 | Bits | Unsigned 4 bits |
| u4AIRandomMax7 | Bits | Unsigned 4 bits |
| u4AIRandomMax8 | Bits | Unsigned 4 bits |
| u4AIRandomMax9 | Bits | Unsigned 4 bits |

## event_flag.wdb
| Field | Type | Description |
| -- | -- | -- |
| iFlagIndex | Int32 | int32 value |

## fieldcamera.wdb
| Field | Type | Description |
| -- | -- | -- |
| fFreeCameraRotationInterporationSpeedAdjustMode | Float32 | float value |
| fFreeCameraRunStopMoveSpeed | Float32 | float value |
| fFreeCameraAimRotationSpeedAtMoving | Float32 | float value |
| fFreeCameraCompositionAimRate | Float32 | float value |
| fFreeCameraAimHeight | Float32 | float value |
| fFreeCameraAimHeightDuringWatchingFoot | Float32 | float value |
| fCollisionSolveInterporationRateX | Float32 | float value |
| fCollisionSolveInterporationRateY | Float32 | float value |
| fCollisionSolveInterporationRateZ | Float32 | float value |
| fInterporationRateAtForward | Float32 | float value |
| fInterporationRateAtBack | Float32 | float value |
| fInterporationRateAtForwardRunning | Float32 | float value |
| fInterporationRateAtBackRunning | Float32 | float value |
| fFreeCameraYAxisRotateAttenuationRateRunning | Float32 | float value |
| fFreeCameraXAxisRotateAttenuationRateRunning | Float32 | float value |
| fFreeCameraYAxisRotateAttenuationRate | Float32 | float value |
| fFreeCameraXAxisRotateAttenuationRate | Float32 | float value |
| fFreeCameraYaxisRotationSpeedRate | Float32 | float value |
| fFreeCameraYaxisRotationSpeedRateAtIdle | Float32 | float value |
| fFreeCameraXaxisRotationSpeedRate | Float32 | float value |
| fFreeCameraXaxisRotationSpeedRateAtIdle | Float32 | float value |
| fFreeCameraFollowingSpeedRate | Float32 | float value |
| fCharacterChangingAlphaTime | Float32 | float value |
| fRailCameraFollowingDistance | Float32 | float value |
| fRailCameraFollowingRate | Float32 | float value |
| fRailCameraYOffset | Float32 | float value |
| fCameraNearZDefault | Float32 | float value |
| fCameraFarZDefault | Float32 | float value |
| fAspectRateDefault | Float32 | float value |
| f9FreeCameraEyeHeight | Bits | signed 9 bits parsed as float value |
| f10EyeAimDistanceAtMoving | Bits | signed 10 bits parsed as float value |
| f10EyeAimDistanceDuringWatchingFoot | Bits | signed 10 bits parsed as float value |
| f10EyeAimDistanceAtStop | Bits | signed 10 bits parsed as float value |
| f14FreeCameraeFov | Bits | signed 14 bits parsed as float value |
| f14CompositAimChangeAngleThrreshold | Bits | signed 14 bits parsed as float value |
| f16DelayTimeBetweenPlayerAndCamera | Bits | signed 16 bits parsed as float value |
| f18CharacterChangingAlphaDistanceMax | Bits | signed 18 bits parsed as float value |
| f14FreeCameraXaxisRotationLimitAngle | Bits | signed 14 bits parsed as float value |
| f18CharacterChangingAlphaDistanceMax_PC | Bits | signed 18 bits parsed as float value |
| f14FreeRailSwitchAngle | Bits | signed 14 bits parsed as float value |
| f18CharacterChangingAlphaDistanceMin | Bits | signed 18 bits parsed as float value |
| f14CameraRadius | Bits | signed 14 bits parsed as float value |
| f18CharacterChangingAlphaDistanceMin_PC | Bits | signed 18 bits parsed as float value |
| f14FreeCameraPullupLimitAngle | Bits | signed 14 bits parsed as float value |
| f19CameraInterporationTimeDefault | Bits | signed 19 bits parsed as float value |
| f18CharacterChangingAlphaLosen | Bits | signed 18 bits parsed as float value |
| f18FreeCameraPullupTimeAtJump | Bits | signed 18 bits parsed as float value |

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
| i8Mulitplier | Bits | Signed 8 bits |
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

## mapset.wdb

N.B: also applies to mapset_loc###.wdb files present inside the db\bg folder

| Field | Type | Description |
| -- | -- | -- |
| iMemorySizeLimit | Int32 | int32 value |
| iVideoMemoryLimit | Int32 | int32 value |
| sScriptIdOnLoaded | UInt32 | relative offset in !!string section |
| sMapNameResourceId | UInt32 | relative offset in !!string section |
| sBattleFreeSpaceResourceId | UInt32 | relative offset in !!string section |
| i20LoadingTime | Bits | Signed 20 bits |
| i11LocationNum | Bits | Signed 11 bits |
| i16FieldSceneDataNum | Bits | Signed 16 bits |
| i16BattleSceneDataNum | Bits | Signed 16 bits |
| i12PartyPositionMarkerGroup | Bits | Signed 12 bits |
| i10FieldMapNum0 | Bits | Signed 10 bits |
| i10FieldMapNum1 | Bits | Signed 10 bits |
| i10FieldMapNum2 | Bits | Signed 10 bits |
| i10FieldMapNum3 | Bits | Signed 10 bits |
| i10FieldMapNum4 | Bits | Signed 10 bits |
| i10FieldMapNum5 | Bits | Signed 10 bits |
| i10FieldMapNum6 | Bits | Signed 10 bits |
| i10FieldMapNum7 | Bits | Signed 10 bits |
| i10FieldMapNum8 | Bits | Signed 10 bits |
| i10FieldMapNum9 | Bits | Signed 10 bits |
| i10FieldMapNum10 | Bits | Signed 10 bits |
| i10FieldMapNum11 | Bits | Signed 10 bits |
| i10FieldMapNum12 | Bits | Signed 10 bits |
| i10FieldMapNum13 | Bits | Signed 10 bits |
| i10FieldMapNum14 | Bits | Signed 10 bits |
| i10FieldMapNum15 | Bits | Signed 10 bits |
| i10FieldMapNum16 | Bits | Signed 10 bits |
| i10FieldMapNum17 | Bits | Signed 10 bits |
| i10FieldMapNum18 | Bits | Signed 10 bits |
| i10FieldMapNum19 | Bits | Signed 10 bits |
| i10VfxMapNum0 | Bits | Signed 10 bits |
| i10VfxMapNum1 | Bits | Signed 10 bits |
| i10VfxMapNum2 | Bits | Signed 10 bits |
| i10VfxMapNum3 | Bits | Signed 10 bits |
| i10BattleMapNum0 | Bits | Signed 10 bits |
| i10BattleMapNum1 | Bits | Signed 10 bits |
| i10BattleMapNum2 | Bits | Signed 10 bits |
| i10BattleMapNum3 | Bits | Signed 10 bits |
| i10BattleMapNum4 | Bits | Signed 10 bits |
| i10BattleMapNum5 | Bits | Signed 10 bits |

## mission.wdb
| Field | Type | Description |
| -- | -- | -- |
| sMissionTitleStringId | UInt32 | relative offset in !!string section |
| sMissionExplanationStringId | UInt32 | relative offset in !!string section |
| sMissionTargetStringId | UInt32 | relative offset in !!string section |
| sMissionPosStringId | UInt32 | relative offset in !!string section |
| sMissionMarkPosStringId | UInt32 | relative offset in !!string section |
| sPosMarkerName | UInt32 | relative offset in !!string section |
| sTreasureBoxId0 | UInt32 | relative offset in !!string section |
| sTreasureBoxId1 | UInt32 | relative offset in !!string section |
| sTreasureBoxId2 | UInt32 | relative offset in !!string section |
| sCharasetId0 | UInt32 | relative offset in !!string section |
| sCharasetId1 | UInt32 | relative offset in !!string section |
| sCharasetId2 | UInt32 | relative offset in !!string section |
| sCharasetId3 | UInt32 | relative offset in !!string section |
| sCharaspecId0 | UInt32 | relative offset in !!string section |
| sCharaspecId1 | UInt32 | relative offset in !!string section |
| sCharaspecId2 | UInt32 | relative offset in !!string section |
| sCharaspecId3 | UInt32 | relative offset in !!string section |
| sCharaspecId4 | UInt32 | relative offset in !!string section |
| sAreaActivationName | UInt32 | relative offset in !!string section |
| iBattleSceneNum | Int32 | int32 value |
| u8ZoneNum | Bits | Unsigned 8 bits |
| u6IndexInMapMenu | Bits | Unsigned 6 bits |
| u4Class | Bits | Unsigned 4 bits |
| u6MissionPictureId | Bits | Unsigned 6 bits |
| u1UnkBool1 | Bits | Unsigned 1 bit |
| u1UnkBool2 | Bits | Unsigned 1 bit |
| u1UnkBool3 | Bits | Unsigned 1 bit |

## monster_book.wdb
| Field | Type | Description |
| -- | -- | -- |
| u6MbookId | Bits | Unsigned 6 bits |
| u9SortId | Bits | Unsigned 9 bits |
| u9PictureId | Bits | Unsigned 9 bits |
| u1UnkBool | Bits | Unsigned 1 bit |

## movie.wdb
| Field | Type | Description |
| -- | -- | -- |
| sZone0 | UInt32 | relative offset in !!string section |
| sZone1 | UInt32 | relative offset in !!string section |

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

## script.wdb

N.B: also applies to script#####.wdb files present inside the db\script folder

| Field | Type | Description |
| -- | -- | -- |
| sClassName | UInt32 | relative offset in !!string section |
| sMethodName | UInt32 | relative offset in !!string section |
| iAdditionalArgCount | Int32 | int32 value |
| iAdditionalArg0 | Int32 | int32 value |
| iAdditionalArg1 | Int32 | int32 value |
| iAdditionalArg2 | Int32 | int32 value |
| iAdditionalArg3 | Int32 | int32 value |
| iAdditionalStringArgCount | Int32 | int32 value |
| sAdditionalStringArg0 | UInt32 | relative offset in !!string section |
| sAdditionalStringArg1 | UInt32 | relative offset in !!string section |
| sAdditionalStringArg2 | UInt32 | relative offset in !!string section |

## shop.wdb
| Field | Type | Description |
| -- | -- | -- |
| sFlagItemId | UInt32 | relative offset in !!string section |
| sUnlockEventID | UInt32 | relative offset in !!string section |
| sShopNameLabel | UInt32 | relative offset in !!string section |
| sSignId | UInt32 | relative offset in !!string section |
| sExplanationLabel | UInt32 | relative offset in !!string section |
| sUnkStringVal1 | UInt32 | relative offset in !!string section |
| sItemLabel1 | UInt32 | relative offset in !!string section |
| sItemLabel2 | UInt32 | relative offset in !!string section |
| sItemLabel3 | UInt32 | relative offset in !!string section |
| sItemLabel4 | UInt32 | relative offset in !!string section |
| sItemLabel5 | UInt32 | relative offset in !!string section |
| sItemLabel6 | UInt32 | relative offset in !!string section |
| sItemLabel7 | UInt32 | relative offset in !!string section |
| sItemLabel8 | UInt32 | relative offset in !!string section |
| sItemLabel9 | UInt32 | relative offset in !!string section |
| sItemLabel10 | UInt32 | relative offset in !!string section |
| sItemLabel11 | UInt32 | relative offset in !!string section |
| sItemLabel12 | UInt32 | relative offset in !!string section |
| sItemLabel13 | UInt32 | relative offset in !!string section |
| sItemLabel14 | UInt32 | relative offset in !!string section |
| sItemLabel15 | UInt32 | relative offset in !!string section |
| sItemLabel16 | UInt32 | relative offset in !!string section |
| sItemLabel17 | UInt32 | relative offset in !!string section |
| sItemLabel18 | UInt32 | relative offset in !!string section |
| sItemLabel19 | UInt32 | relative offset in !!string section |
| sItemLabel20 | UInt32 | relative offset in !!string section |
| sItemLabel21 | UInt32 | relative offset in !!string section |
| sItemLabel22 | UInt32 | relative offset in !!string section |
| sItemLabel23 | UInt32 | relative offset in !!string section |
| sItemLabel24 | UInt32 | relative offset in !!string section |
| sItemLabel25 | UInt32 | relative offset in !!string section |
| sItemLabel26 | UInt32 | relative offset in !!string section |
| sItemLabel27 | UInt32 | relative offset in !!string section |
| sItemLabel28 | UInt32 | relative offset in !!string section |
| sItemLabel29 | UInt32 | relative offset in !!string section |
| sItemLabel30 | UInt32 | relative offset in !!string section |
| sItemLabel31 | UInt32 | relative offset in !!string section |
| sItemLabel32 | UInt32 | relative offset in !!string section |
| u4Version | Bits | Unsigned 4 bits |
| u13ZoneNum | Bits | Unsigned 13 bits |

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

## succession.wdb
| Field | Type | Description |
| -- | -- | -- |
| u1RideOffChocobo | Bits | Unsigned 1 bit |
| i2NaviMapMode | Bits | Signed 2 bits |
| i2PartyCharaAIMode | Bits | Signed 2 bits |
| i2UserControlMode | Bits | Signed 2 bits |
| i9ZoneStateChangeTriggerOnEnter | Bits | Signed 9 bits |
| i9ZoneStateWait | Bits | Signed 9 bits |
| u1EventSkipAble | Bits | Unsigned 1 bit |
| u1FieldCommonObjectHide | Bits | Unsigned 1 bit |
| u1EnablePause | Bits | Unsigned 1 bit |
| u1SuspendFieldObject | Bits | Unsigned 1 bit |
| u1DisableTalk | Bits | Unsigned 1 bit |
| i9ZoneStateChangeTriggerOnExit | Bits | Signed 9 bits |
| i9ZoneStateExit | Bits | Signed 9 bits |
| u13CameraInterporationTimeOnEnter | Bits | Unsigned 13 bits |
| u1FieldActiveFlag | Bits | Unsigned 1 bit |
| u13CameraInterporationTimeOnExit | Bits | Unsigned 13 bits |
| u1HighModelEventFlag | Bits | Unsigned 1 bit |
| u1ApplyFieldCameraByPlayerMatrix | Bits | Unsigned 1 bit |

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