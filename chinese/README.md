# Chinese stroke and parts data

`strokes.js` holds the stroke data the app uses to draw and check Chinese characters: for each character in the word list (simplified and traditional forms), the stroke outlines (`strokes`) and their centre lines (`medians`). It defines one global, `DATA`, so the app can load it with a plain `<script>` tag.

A public copy of this folder is at https://github.com/mingming-app/stroke-data (folder `chinese/`).

## Source

- **Make Me a Hanzi** by Shaunak Kishore: https://github.com/skishore/makemeahanzi
  Copyright 1999 Arphic Technology Co., Ltd., copyright 2016 Shaunak Kishore.
- Derived from the **Arphic PL KaitiM GB** and **Arphic PL KaitiM Big5** fonts, copyright 1999 Arphic Technology Co., Ltd.
- Taken from the **hanzi-writer-data** package, version 2.0.1, by David Chanin: https://github.com/chanind/hanzi-writer-data

## Licence

Arphic Public License. The full text is in `ARPHICPL.TXT` in this folder. You may copy, change and redistribute this data under its terms.

## Changes

Changed from hanzi-writer-data 2.0.1, first in November 2026:

- Only the characters in the app's word list are kept.
- Only the `strokes` and `medians` fields are kept. The `radStrokes` field is dropped.
- The per-character JSON files are combined into one JavaScript file.

The stroke shapes themselves are not changed. `tools/build-strokes.js` in the app's repository rebuilds the file from the package, so the change can be repeated exactly.

# Parts data

`parts.js` says how each character breaks down into its parts, one level at a time, for the app's Parts first choice and its parts animation. It defines two globals: `PARTS` (for each character: its parts, which part each stroke belongs to, and for a sound-meaning character, which part gives the meaning and which the sound) and `PART_INFO` (for each part: its meaning and pinyin, and for a side form such as 亻, the full character it stands for).

## Source

- **Make Me a Hanzi**'s `dictionary.txt`, commit bddc96d4: https://github.com/skishore/makemeahanzi
  It is derived from the Unihan database (copyright 1991-2009 Unicode, Inc.) and CJKlib. The Unicode notice is at the top of `LGPL.txt`.

## Licence

GNU Lesser General Public License, version 3 or later: `LGPL.txt` (which starts with the Unicode notice). The LGPL builds on the GNU General Public License, in `GPL.txt`.

## Changes

Changed from `dictionary.txt`, first in November 2026:

- Only the characters in the app's word list, and the parts they break into, are kept.
- Only the decomposition, the stroke-to-part matches, the first pinyin, the meaning (cut to its first sense) and, for sound-meaning characters, which part gives the meaning and which the sound, are kept, in a shorter form. The etymology hints are left out.
- Side forms are marked with the full character they stand for, and each part is marked as learnable (it has stroke data) and as common (in the 3,500 common characters of the Table of General Standard Chinese Characters).

`tools/build-parts.js` in the app's repository rebuilds the file, so the change can be repeated exactly.
