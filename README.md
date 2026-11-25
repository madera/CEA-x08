# CEA-x08

EIA-608 and CEA-708 test files for conformance testing.

Two reference videos, **22 tests each, 44 in total**. Every frame carries three
things at once:

- the captions under test, as your decoder draws them;
- a reference panel for each channel or service, showing what a conformant
  decoder must display at that instant;
- the caption bytes on the wire, decoded and annotated, with a running timecode.

One frame is therefore enough to judge a decoder. There is no separate reference
to line up against, and no need to trust a transcript.

## EIA-608

Line 21 captions. Four caption channels across the two fields, each in a
different language, so channel mix-ups are obvious.

| channel | field | language |
|---------|-------|----------|
| CC1 | 1 | English |
| CC2 | 1 | Spanish |
| CC3 | 2 | Portuguese |
| CC4 | 2 | French |

Runs 7 min 39 s.

| # | test | at |
|---|------|----|
| 1 | Title | 0:00 |
| 2 | Pop-on: two memories | 0:16 |
| 3 | Roll-up | 0:36 |
| 4 | Roll-up: base row and indent | 1:00 |
| 5 | Live roll-up: an interview | 1:20 |
| 6 | Paint-on | 1:55 |
| 7 | Pop-on, paint-on and roll-up together | 2:09 |
| 8 | The grid: 15 rows, 32 columns, 8 indents | 2:27 |
| 9 | Positioning: PACs and tabs | 2:55 |
| 10 | Colours | 3:13 |
| 11 | Italics, underline, flash | 3:27 |
| 12 | Backgrounds, transparency, foreground black | 3:43 |
| 13 | The standard character set | 4:01 |
| 14 | Special and extended characters | 4:15 |
| 15 | Editing: backspace and delete | 4:31 |
| 16 | Erase: EDM and ENM | 4:47 |
| 17 | Row end and cursor rules | 5:01 |
| 18 | Four channels on two fields | 5:15 |
| 19 | XDS packets on field 2 | 5:35 |
| 20 | Text-mode services | 5:49 |
| 21 | On the wire: parity and doubling | 7:07 |
| 22 | Closing | 7:23 |

## CEA-708

DTVCC captions. Sixteen services run at the same time, which also exercises
bandwidth sharing and the character sets of each writing system.

| service | language | | service | language |
|---------|----------|---|---------|----------|
| 1 | English | | 9 | Greek |
| 2 | Spanish | | 10 | Polish |
| 3 | Portuguese | | 11 | Vietnamese |
| 4 | Japanese | | 12 | Turkish |
| 5 | French | | 13 | Chinese, simplified |
| 6 | German | | 14 | Chinese, traditional |
| 7 | Italian | | 15 | Korean, Unicode |
| 8 | Russian | | 16 | Korean, EUC-KR |

Runs 5 min 16 s.

| # | test | at |
|---|------|----|
| 1 | Title | 0:00 |
| 2 | Pop-on captions | 0:20 |
| 3 | Roll-up captions | 0:34 |
| 4 | Paint-on captions | 0:48 |
| 5 | Eight windows, nine anchors | 1:00 |
| 6 | Speakers, sounds and music | 1:18 |
| 7 | 64 colours | 1:30 |
| 8 | Opacity | 1:44 |
| 9 | Font styles | 1:56 |
| 10 | Pen sizes and offsets | 2:10 |
| 11 | Italics, underline and edges | 2:22 |
| 12 | Window fills and borders | 2:36 |
| 13 | Justification | 2:50 |
| 14 | Print and scroll directions | 3:02 |
| 15 | Display effects | 3:16 |
| 16 | Characters and symbols | 3:32 |
| 17 | Delays | 3:44 |
| 18 | Hide, show, toggle, clear, delete | 3:58 |
| 19 | CEA-608 compatibility | 4:16 |
| 20 | Several services | 4:30 |
| 21 | Bandwidth and timing | 4:44 |
| 22 | Closing | 4:58 |

## Download

The videos are large, so they are published as a release rather than committed
to the repository.

**[Download v3.0](https://github.com/madera/CEA-x08/releases/tag/v3.0)** ·
[all releases](https://github.com/madera/CEA-x08/releases)

Six files, each at 30 and 60 fps:

| file | aspect | size |
|------|--------|------|
| `EIA-608_CC_Validator_16x9-30fps-4K.mp4` | 16:9, 3840x2160 | 152 MB |
| `EIA-608_CC_Validator_16x9-60fps-4K.mp4` | 16:9, 3840x2160 | 267 MB |
| `EIA-608_CC_Validator_4x3-30fps.mp4` | 4:3, 1440x1080 | 60 MB |
| `EIA-608_CC_Validator_4x3-60fps.mp4` | 4:3, 1440x1080 | 98 MB |
| `CEA-708_CC_Validator_16x9-30fps-4K.mp4` | 16:9, 3840x2160 | 89 MB |
| `CEA-708_CC_Validator_16x9-60fps-4K.mp4` | 16:9, 3840x2160 | 94 MB |

The captions are carried as A/53 caption data in the H.264 SEI, so a decoder
reaches them the same way it would from a broadcast. The timecodes above are
the same in every variant.

**Why EIA-608 also ships in 4:3.** Its safe caption area is defined on a 4:3
picture: 32 columns across 80 % of that width. On a 16:9 picture the 4:3 plane
sits pillarboxed in the centre, and a decoder that instead spreads the 32
columns over the full 16:9 width draws captions a third too wide. The 4:3 files
exercise the same decoder without that trap, so the two sets together tell you
whether a failure is in the layout or in the plane. The CEA-708 set is 16:9
only.

## License

MIT. Copyright (c) 2026 Rodrigo Madera.
