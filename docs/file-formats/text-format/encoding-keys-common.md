This page contains encoding keys used by all the games from the trilogy.

### Single byte keys

These keys represent special conditions that are taken into account by the games when displaying them. each key would have to be inserted right before a sequence of text that you want to modify.

| Byte | Key | Purpose |
| --- | --- | --- |
| 0x00 | {End} | Purpose unknown |
| 0x01 | {Escape} | Purpose unknown |
| 0x02 | {Italic} | Styles the text following this key to be italic |
| 0x03 | {StraightLine} | Inserts a small horizontal line |
| 0x04 | {Article} | Purpose unknown |
| 0x05 | {ArticleMany} | Purpose unknown |
| 0xFF | {FF} | Padding |


### Characters byte keys
These keys are used for representing special characters that are present only in latin encodings. as all the encodings supported by the games lacks these special characters, these keys are used for representing them thereby allowing the games to use them in all of its encodings.

#### Group 1
**Important:** For English (us), French (fr), German (gr), Italian (it), Japanese (jp), and Spanish (sp) ztr files.

| Byte | Key / Char | Purpose |
| --- | --- | --- |
| 0x85, 0x40 | {€} | Inserts character  € |
| 0x85, 0x42 | {‚} | Inserts character  ‚ |
| 0x85, 0x44 | {„} | Inserts character  „ |
| 0x85, 0x45 | {…} | Inserts character  … |
| 0x85, 0x46 | {†} | Inserts character  † |
| 0x85, 0x47 | {‡} | Inserts character  ‡ |
| 0x85, 0x49 | {‰} | Inserts character  ‰ |
| 0x85, 0x4A | {Š} | Inserts character  Š |
| 0x85, 0x4B | {‹} | Inserts character  ‹ |
| 0x85, 0x4C | {Œ} | Inserts character  Œ |
| 0x85, 0x4E | {Ž} | Inserts character  Ž |
| 0x85, 0x51 | {‘} | Inserts character  ‘ |
| 0x85, 0x52 | {’} | Inserts character  ’ |
| 0x85, 0x53 | {“} | Inserts character  “ |
| 0x85, 0x54 | {”} | Inserts character  ” |
| 0x85, 0x55 | {•} | Inserts character  • |
| 0x85, 0x56 | {-} | Inserts character  - |
| 0x85, 0x57 | {—} | Inserts character  — |
| 0x85, 0x59 | {™} | Inserts character  ™ |
| 0x85, 0x5A | {š} | Inserts character  š |
| 0x85, 0x5B | {›} | Inserts character  › |
| 0x85, 0x5C | {œ} | Inserts character  œ |
| 0x85, 0x5E | {ž} | Inserts character  ž |
| 0x85, 0x5F | {Ÿ} | Inserts character  Ÿ |
| 0x85, 0x61 | {¡} | Inserts character  ¡ |
| 0x85, 0x62 | {¢} | Inserts character  ¢ |
| 0x85, 0x63 | {£} | Inserts character  £ |
| 0x85, 0x64 | {¤} | Inserts character  ¤ |
| 0x85, 0x65 | {¥} | Inserts character  ¥ |
| 0x85, 0x66 | {¦} | Inserts character  ¦ |
| 0x85, 0x67 | {§} | Inserts character  § |
| 0x85, 0x68 | {¨} | Inserts character  ¨ |
| 0x85, 0x69 | {©} | Inserts character  © |
| 0x85, 0x6A | {ª} | Inserts character  ª |
| 0x85, 0x6B | {«} | Inserts character  « |
| 0x85, 0x6C | {¬} | Inserts character  ¬ |
| 0x85, 0x6E | {®} | Inserts character  ® |
| 0x85, 0x6F | {¯} | Inserts character  ¯ |
| 0x85, 0x70 | {°} | Inserts character  ° |
| 0x85, 0x71 | {±} | Inserts character  ± |
| 0x85, 0x72 | {²} | Inserts character  ² |
| 0x85, 0x73 | {³} | Inserts character  ³ |
| 0x85, 0x74 | {´} | Inserts character  ´ |
| 0x85, 0x75 | {µ} | Inserts character  µ |
| 0x85, 0x76 | {¶} | Inserts character  ¶ |
| 0x85, 0x77 | {·} | Inserts character  · |
| 0x85, 0x78 | {¸} | Inserts character  ¸ |
| 0x85, 0x79 | {¹} | Inserts character  ¹ |
| 0x85, 0x7A | {º} | Inserts character  º |
| 0x85, 0x7B | {»} | Inserts character  » |
| 0x85, 0x7C | {¼} | Inserts character  ¼ |
| 0x85, 0x7D | {½} | Inserts character  ½ |
| 0x85, 0x7E | {¾} | Inserts character  ¾ |
| 0x85, 0x7F | {¿} | Inserts character  ¿ |
| 0x85, 0x9F | {À} | Inserts character  À |
| 0x85, 0x81 | {Á} | Inserts character  Á |
| 0x85, 0x82 | {Â} | Inserts character  Â |
| 0x85, 0x83 | {Ã} | Inserts character  Ã |
| 0x85, 0x84 | {Ä} | Inserts character  Ä |
| 0x85, 0x85 | {Å} | Inserts character  Å |
| 0x85, 0x86 | {Æ} | Inserts character  Æ |
| 0x85, 0x87 | {Ç} | Inserts character  Ç |
| 0x85, 0x88 | {È} | Inserts character  È |
| 0x85, 0x89 | {É} | Inserts character  É |
| 0x85, 0x8A | {Ê} | Inserts character  Ê |
| 0x85, 0x8B | {Ë} | Inserts character  Ë |
| 0x85, 0x8C | {Ì} | Inserts character  Ì |
| 0x85, 0x8D | {Í} | Inserts character  Í |
| 0x85, 0x8E | {Î} | Inserts character  Î |
| 0x85, 0x8F | {Ï} | Inserts character  Ï |
| 0x85, 0x90 | {Ð} | Inserts character  Ð |
| 0x85, 0x91 | {Ñ} | Inserts character  Ñ |
| 0x85, 0x92 | {Ò} | Inserts character  Ò |
| 0x85, 0x93 | {Ó} | Inserts character  Ó |
| 0x85, 0x94 | {Ô} | Inserts character  Ô |
| 0x85, 0x95 | {Õ} | Inserts character  Õ |
| 0x85, 0x96 | {Ö} | Inserts character  Ö |
| 0x85, 0xB6 | {×} | Inserts character  × |
| 0x85, 0x98 | {Ø} | Inserts character  Ø |
| 0x85, 0x99 | {Ù} | Inserts character  Ù |
| 0x85, 0x9A | {Ú} | Inserts character  Ú |
| 0x85, 0x9B | {Û} | Inserts character  Û |
| 0x85, 0x9C | {Ü} | Inserts character  Ü |
| 0x85, 0x9D | {Ý} | Inserts character  Ý |
| 0x85, 0xBD | {Þ} | Inserts character  Þ |
| 0x85, 0xBE | {ß} | Inserts character  ß |
| 0x85, 0xBF | {à} | Inserts character  à |
| 0x85, 0xC0 | {á} | Inserts character  á |
| 0x85, 0xC1 | {â} | Inserts character  â |
| 0x85, 0xC2 | {ã} | Inserts character  ã |
| 0x85, 0xC3 | {ä} | Inserts character  ä |
| 0x85, 0xC4 | {å} | Inserts character  å |
| 0x85, 0xC5 | {æ} | Inserts character  æ |
| 0x85, 0xC6 | {ç} | Inserts character  ç |
| 0x85, 0xC7 | {è} | Inserts character  è |
| 0x85, 0xC8 | {é} | Inserts character  é |
| 0x85, 0xC9 | {ê} | Inserts character  ê |
| 0x85, 0xCA | {ë} | Inserts character  ë |
| 0x85, 0xCB | {ì} | Inserts character  ì |
| 0x85, 0xCC | {í} | Inserts character  í |
| 0x85, 0xCD | {î} | Inserts character  î |
| 0x85, 0xCE | {ï} | Inserts character  ï |
| 0x85, 0xCF | {ð} | Inserts character  ð |
| 0x85, 0xD0 | {ñ} | Inserts character  ñ |
| 0x85, 0xD1 | {ò} | Inserts character  ò |
| 0x85, 0xD2 | {ó} | Inserts character  ó |
| 0x85, 0xD3 | {ô} | Inserts character  ô |
| 0x85, 0xD4 | {õ} | Inserts character  õ |
| 0x85, 0xD5 | {ö} | Inserts character  ö |
| 0x85, 0xD6 | {÷} | Inserts character  ÷ |
| 0x85, 0xD7 | {ø} | Inserts character  ø |
| 0x85, 0xD8 | {ù} | Inserts character  ù |
| 0x85, 0xD9 | {ú} | Inserts character  ú |
| 0x85, 0xDA | {û} | Inserts character  û |
| 0x85, 0xDB | {ü} | Inserts character  ü |
| 0x85, 0xDC | {ý} | Inserts character  ý |
| 0x85, 0xDD | {þ} | Inserts character  þ |
| 0x85, 0xDE | {ÿ} | Inserts character  ÿ |

#### Group 2
**Important:** For Chinese (ch) and Korean (kr) ztr files.

| Byte | Key / Char | Purpose |
| --- | --- | --- |
| 0x80, 0x40 | {€} | Inserts character € |
| 0x80, 0x42 | {‚} | Inserts character ‚ |
| 0x80, 0x44 | {„} | Inserts character „ |
| 0x80, 0x45 | {…} | Inserts character … |
| 0x80, 0x46 | {†} | Inserts character † |
| 0x80, 0x47 | {‡} | Inserts character ‡ |
| 0x80, 0x49 | {‰} | Inserts character ‰ |
| 0x80, 0x4A | {Š} | Inserts character Š |
| 0x80, 0x4B | {‹} | Inserts character ‹ |
| 0x80, 0x4C | {Œ} | Inserts character Œ |
| 0x80, 0x4E | {Ž} | Inserts character Ž |
| 0x80, 0x51 | {‘} | Inserts character ‘ |
| 0x80, 0x52 | {’} | Inserts character ’ |
| 0x80, 0x53 | {“} | Inserts character “ |
| 0x80, 0x54 | {”} | Inserts character ” |
| 0x80, 0x55 | {•} | Inserts character • |
| 0x80, 0x56 | {-} | Inserts character - |
| 0x80, 0x57 | {—} | Inserts character — |
| 0x80, 0x59 | {™} | Inserts character ™ |
| 0x80, 0x5A | {š} | Inserts character š |
| 0x80, 0x5B | {›} | Inserts character › |
| 0x80, 0x5C | {œ} | Inserts character œ |
| 0x80, 0x5E | {ž} | Inserts character ž |
| 0x80, 0x5F | {Ÿ} | Inserts character Ÿ |
| 0x80, 0x61 | {¡} | Inserts character ¡ |
| 0x80, 0x62 | {¢} | Inserts character ¢ |
| 0x80, 0x63 | {£} | Inserts character £ |
| 0x80, 0x64 | {¤} | Inserts character ¤ |
| 0x80, 0x65 | {¥} | Inserts character ¥ |
| 0x80, 0x66 | {¦} | Inserts character ¦ |
| 0x80, 0x67 | {§} | Inserts character § |
| 0x80, 0x68 | {¨} | Inserts character ¨ |
| 0x80, 0x69 | {©} | Inserts character © |
| 0x80, 0x6A | {ª} | Inserts character ª |
| 0x80, 0x6B | {«} | Inserts character « |
| 0x80, 0x6C | {¬} | Inserts character ¬ |
| 0x80, 0x6E | {®} | Inserts character ® |
| 0x80, 0x6F | {¯} | Inserts character ¯ |
| 0x80, 0x70 | {°} | Inserts character ° |
| 0x80, 0x71 | {±} | Inserts character ± |
| 0x80, 0x72 | {²} | Inserts character ² |
| 0x80, 0x73 | {³} | Inserts character ³ |
| 0x80, 0x74 | {´} | Inserts character ´ |
| 0x80, 0x75 | {µ} | Inserts character µ |
| 0x80, 0x76 | {¶} | Inserts character ¶ |
| 0x80, 0x77 | {·} | Inserts character · |
| 0x80, 0x78 | {¸} | Inserts character ¸ |
| 0x80, 0x79 | {¹} | Inserts character ¹ |
| 0x80, 0x7A | {º} | Inserts character º |
| 0x80, 0x7B | {»} | Inserts character » |
| 0x80, 0x7C | {¼} | Inserts character ¼ |
| 0x80, 0x7D | {½} | Inserts character ½ |
| 0x80, 0x7E | {¾} | Inserts character ¾ |
| 0x80, 0x7F | {¿} | Inserts character ¿ |
| 0x80, 0x9F | {À} | Inserts character À |
| 0x80, 0x81 | {Á} | Inserts character Á |
| 0x80, 0x82 | {Â} | Inserts character Â |
| 0x80, 0x83 | {Ã} | Inserts character Ã |
| 0x80, 0x84 | {Ä} | Inserts character Ä |
| 0x80, 0x85 | {Å} | Inserts character Å |
| 0x80, 0x86 | {Æ} | Inserts character Æ |
| 0x80, 0x87 | {Ç} | Inserts character Ç |
| 0x80, 0x88 | {È} | Inserts character È |
| 0x80, 0x89 | {É} | Inserts character É |
| 0x80, 0x8A | {Ê} | Inserts character Ê |
| 0x80, 0x8B | {Ë} | Inserts character Ë |
| 0x80, 0x8C | {Ì} | Inserts character Ì |
| 0x80, 0x8D | {Í} | Inserts character Í |
| 0x80, 0x8E | {Î} | Inserts character Î |
| 0x80, 0x8F | {Ï} | Inserts character Ï |
| 0x80, 0x90 | {Ð} | Inserts character Ð |
| 0x80, 0x91 | {Ñ} | Inserts character Ñ |
| 0x80, 0x92 | {Ò} | Inserts character Ò |
| 0x80, 0x93 | {Ó} | Inserts character Ó |
| 0x80, 0x94 | {Ô} | Inserts character Ô |
| 0x80, 0x95 | {Õ} | Inserts character Õ |
| 0x80, 0x96 | {Ö} | Inserts character Ö |
| 0x80, 0xB6 | {×} | Inserts character × |
| 0x80, 0x98 | {Ø} | Inserts character Ø |
| 0x80, 0x99 | {Ù} | Inserts character Ù |
| 0x80, 0x9A | {Ú} | Inserts character Ú |
| 0x80, 0x9B | {Û} | Inserts character Û |
| 0x80, 0x9C | {Ü} | Inserts character Ü |
| 0x80, 0x9D | {Ý} | Inserts character Ý |
| 0x80, 0xBD | {Þ} | Inserts character Þ |
| 0x80, 0xBE | {ß} | Inserts character ß |
| 0x80, 0xBF | {à} | Inserts character à |
| 0x80, 0xC0 | {á} | Inserts character á |
| 0x80, 0xC1 | {â} | Inserts character â |
| 0x80, 0xC2 | {ã} | Inserts character ã |
| 0x80, 0xC3 | {ä} | Inserts character ä |
| 0x80, 0xC4 | {å} | Inserts character å |
| 0x80, 0xC5 | {æ} | Inserts character æ |
| 0x80, 0xC6 | {ç} | Inserts character ç |
| 0x80, 0xC7 | {è} | Inserts character è |
| 0x80, 0xC8 | {é} | Inserts character é |
| 0x80, 0xC9 | {ê} | Inserts character ê |
| 0x80, 0xCA | {ë} | Inserts character ë |
| 0x80, 0xCB | {ì} | Inserts character ì |
| 0x80, 0xCC | {í} | Inserts character í |
| 0x80, 0xCD | {î} | Inserts character î |
| 0x80, 0xCE | {ï} | Inserts character ï |
| 0x80, 0xCF | {ð} | Inserts character ð |
| 0x80, 0xD0 | {ñ} | Inserts character ñ |
| 0x80, 0xD1 | {ò} | Inserts character ò |
| 0x80, 0xD2 | {ó} | Inserts character ó |
| 0x80, 0xD3 | {ô} | Inserts character ô |
| 0x80, 0xD4 | {õ} | Inserts character õ |
| 0x80, 0xD5 | {ö} | Inserts character ö |
| 0x80, 0xD6 | {÷} | Inserts character ÷ |
| 0x80, 0xD7 | {ø} | Inserts character ø |
| 0x80, 0xD8 | {ù} | Inserts character ù |
| 0x80, 0xD9 | {ú} | Inserts character ú |
| 0x80, 0xDA | {û} | Inserts character û |
| 0x80, 0xDB | {ü} | Inserts character ü |
| 0x80, 0xDC | {ý} | Inserts character ý |
| 0x80, 0xDD | {þ} | Inserts character þ |
| 0x80, 0xDE | {ÿ} | Inserts character ÿ |


### Similar character byte keys
N.B.: These are duplicate keys that are used for representing special characters present in latin only encodings.

| Byte | Key | Purpose |
| --- | --- | --- |
| 0x85, 0x80 | {ExChara85 80} | Inserts character ¿ |
| 0x85, 0x97 | {ExChara85 97} | Inserts character × |
| 0x85, 0xA0 | {ExChara85 A0} | Inserts character Á |
| 0x85, 0xA1 | {ExChara85 A1} | Inserts character Â |
| 0x85, 0xA2 | {ExChara85 A2} | Inserts character Ã |
| 0x85, 0xA3 | {ExChara85 A3} | Inserts character Ä |
| 0x85, 0xA4 | {ExChara85 A4} | Inserts character Å |
| 0x85, 0xA5 | {ExChara85 A5} | Inserts character Æ |
| 0x85, 0xA6 | {ExChara85 A6} | Inserts character Ç |
| 0x85, 0xA7 | {ExChara85 A7} | Inserts character È |
| 0x85, 0xA8 | {ExChara85 A8} | Inserts character É |
| 0x85, 0xA9 | {ExChara85 A9} | Inserts character Ê |
| 0x85, 0xAA | {ExChara85 AA} | Inserts character Ë |
| 0x85, 0xAB | {ExChara85 AB} | Inserts character Ì |
| 0x85, 0xAC | {ExChara85 AC} | Inserts character Í |
| 0x85, 0xAD | {ExChara85 AD} | Inserts character Î |
| 0x85, 0xAE | {ExChara85 AE} | Inserts character Ï |
| 0x85, 0xAF | {ExChara85 AF} | Inserts character Ð |
| 0x85, 0xB0 | {ExChara85 B0} | Inserts character Ñ |
| 0x85, 0xB1 | {ExChara85 B1} | Inserts character Ò |
| 0x85, 0xB2 | {ExChara85 B2} | Inserts character Ó |
| 0x85, 0xB3 | {ExChara85 B3} | Inserts character Ô |
| 0x85, 0xB4 | {ExChara85 B4} | Inserts character Õ |
| 0x85, 0xB5 | {ExChara85 B5} | Inserts character Ö |
| 0x85, 0xB7 | {ExChara85 B7} | Inserts character Ø |
| 0x85, 0xB8 | {ExChara85 B8} | Inserts character Ù |
| 0x85, 0xB9 | {ExChara85 B9} | Inserts character Ú |
| 0x85, 0xBA | {ExChara85 BA} | Inserts character Û |
| 0x85, 0xBB | {ExChara85 BB} | Inserts character Ü |
| 0x85, 0xBC | {ExChara85 BC} | Inserts character Ý |

### Special byte keys
Just like the [Single byte keys](#single-byte-keys), these keys also represent special conditions that are taken into account by the games when displaying them.

#### Group 1
**Important:** For English (us), French (fr), German (gr), Italian (it), Japanese (jp), and Spanish (sp) ztr files.

| Byte | Key | Purpose |
| --- | --- | --- |
| 0x40, 0x70 | {Text NewPage} | Purpose unknown |
| 0x40, 0x72 | {Text NewLine} | Moves the text following this key to a newline |
| 0x85, 0x60 | {Text Tab} | Purpose unknown | 		   
| 0xF4, 0x40 | {Entity 1} | Entity or object name that is displayed ingame with the text following this key |
| 0xF4, 0x41 | {Entity 2} | Entity or object name that is displayed ingame with the text following this key |
| 0xF4, 0x42 | {Entity 3} | Entity or object name that is displayed ingame with the text following this key |
| 0xF4, 0x43 | {Entity 4} | Entity or object name that is displayed ingame with the text following this key | 		   
| 0xF6, 0x40 | {Key Entity} | Key Entity or object name that is displayed ingame with the text following this key | 		   
| 0xF7, 0x40 | {Counter Type 1} | Used when displaying text that has a numerical value |
| 0xF7, 0x41 | {Counter Type 2} | Used when displaying text that has a numerical value |
| 0xF7, 0x42 | {Counter Type 3} | Used when displaying text that has a numerical value |

#### Group 2
**Important:** For Chinese (ch) ztr files.

| Byte | Key | Purpose |
| --- | --- | --- |
| 0x40, 0x70 | {Text NewPage} | Purpose unknown |
| 0x40, 0x72 | {Text NewLine} | Moves the text following this key to a newline |
| 0x85, 0x60 | {Text Tab} | Purpose unknown |
| 0xFC, 0x40 | {Entity 1} | Entity or object name that is displayed ingame with the text following this key |
| 0xFC, 0x41 | {Entity 2} | Entity or object name that is displayed ingame with the text following this key |
| 0xFC, 0x42 | {Entity 3} | Entity or object name that is displayed ingame with the text following this key |
| 0xFC, 0x43 | {Entity 4} | Entity or object name that is displayed ingame with the text following this key |
| 0xFD, 0x40 | {Counter Type 1} | Used when displaying text that has a numerical value |
| 0xFD, 0x41 | {Counter Type 2} | Used when displaying text that has a numerical value |
| 0xFD, 0x42 | {Counter Type 3} | Used when displaying text that has a numerical value | 

#### Group 3
**Important:** For Korean (kr) ztr files.

| Byte | Key | Purpose |
| --- | --- | --- |
| 0x40, 0x70 | {Text NewPage} | Purpose unknown |
| 0x40, 0x72 | {Text NewLine} | Moves the text following this key to a newline |
| 0x85, 0x60 | {Text Tab} | Purpose unknown |
| 0xAA, 0xA1 | {Entity 1} | Entity or object name that is displayed ingame with the text following this key |
| 0xAA, 0xA2 | {Entity 2} | Entity or object name that is displayed ingame with the text following this key |
| 0xAA, 0xA3 | {Entity 3} | Entity or object name that is displayed ingame with the text following this key |
| 0xAA, 0xA4 | {Entity 4} | Entity or object name that is displayed ingame with the text following this key |
| 0xAB, 0xA1 | {Counter Type 1} | Used when displaying text that has a numerical value |
| 0xAB, 0xA2 | {Counter Type 2} | Used when displaying text that has a numerical value |
| 0xAB, 0xA3 | {Counter Type 3} | Used when displaying text that has a numerical value |


### Unknown byte keys
N.B.: The purpose of these two byte keys are unknown.

| Byte | Key |
| --- | --- |
| 0x81, 0x40 | {Unk81 40} |
| 0xFA, 0x20 | {UnkFA 20} |
| 0xFF, 0x86 | {UnkFF 86} |
| 0xFF, 0x90 | {UnkFF 90} |
| 0xFF, 0x91 | {UnkFF 91} |
| 0xFF, 0x93 | {UnkFF 93} |
| 0xFF, 0x94 | {UnkFF 94} |
| 0xFF, 0x99 | {UnkFF 99} |
| 0xFF, 0x9A | {UnkFF 9A} |
| 0xFF, 0x9B | {UnkFF 9B} |
| 0xFF, 0x9D | {UnkFF 9D} |
| 0xFF, 0x9E | {UnkFF 9E} |
| 0xFF, 0xA9 | {UnkFF A9} |
| 0xFF, 0xB8 | {UnkFF B8} |
| 0xFF, 0xC9 | {UnkFF C9} |
| 0xFF, 0xCC | {UnkFF CC} |
| 0xFF, 0xCE | {UnkFF CE} |
| 0xFF, 0xD0 | {UnkFF D0} |
| 0xFF, 0xD3 | {UnkFF D3} |
| 0xFF, 0xDA | {UnkFF DA} |
| 0xFF, 0xDD | {UnkFF DD} |
| 0xFF, 0xE0 | {UnkFF E0} |
| 0xFF, 0xE3 | {UnkFF E3} |
| 0xFF, 0xE4 | {UnkFF E4} |
| 0xFF, 0xE6 | {UnkFF E6} |
| 0xFF, 0xF1 | {UnkFF F1} |
| 0xFF, 0x82 | {UnkFF 82} |
| 0xFF, 0x83 | {UnkFF 83} |
| 0xFF, 0x8F | {UnkFF 8F} |
| 0xFF, 0x96 | {UnkFF 96} |

### Unknown2 byte keys
N.B.: The purpose of these two byte keys are unknown.

| Byte | Key |
| --- | --- |
| 0xF1, 0x78 | {Unk2_F1 78} |
| 0xF4, 0x44 | {Unk2_F4 44} |
| 0xF4, 0x45 | {Unk2_F4 45} |
| 0xF4, 0x46 | {Unk2_F4 46} |
| 0xF4, 0x47 | {Unk2_F4 47} |
| 0xF4, 0x48 | {Unk2_F4 48} |
| 0xF4, 0x49 | {Unk2_F4 49} |
| 0xF4, 0x60 | {Unk2_F4 60} |
| 0xF5, 0x40 | {Unk2_F5 40} |
| 0xF6, 0x60 | {Unk2_F6 60} |