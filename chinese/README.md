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

# Pronunciation recordings: audio/ and audio.js

`audio/` holds a recording for each word and learnable part the app teaches, as 64 kbit/s MP3 files; `audio.js` defines `AUDIO`, which maps each word's or part's characters (simplified and traditional) to its file name.

## Sources

- **audio-cmn** by Hugo Lopez et al. (PLIDAM, INALCO): https://github.com/hugolpz/audio-cmn, 64k files. Licence: Creative Commons Attribution-ShareAlike (CC BY-SA), as audio-cmn states for both sets (https://creativecommons.org/licenses/by-sa/4.0/; the version of the original pack's licence is still to be confirmed from its readme, http://packs.shtooka.net/cmn-caen-tan/readme.txt, offline on 20 Nov 2026).
  - HSK words and characters read by **Yue Tan** (from the Shtooka project's cmn-caen-tan pack, recorded with Nicolas Vion's software).
  - Mandarin syllables in each tone ("syllabs v.2") read by **Chen Wang**.
- **Lingua Libre** (https://lingualibre.org), on Wikimedia Commons: seven words audio-cmn lacks (北京, 不客气, 出租车, 打电话, 下雨, 中国, 哪儿), read by **CanonNi**, files "LL-Q9192 (cmn)-CanonNi-<word>.wav". Licence: CC0 (public domain).

## Changes

Changed from audio-cmn, first in November 2026:

- Only the recordings the app uses are kept, renamed: a word by its characters (朋友.mp3), a syllable by its pinyin and tone number (ai4.mp3).
- A single character or part read its usual way (the first reading pypinyin lists) plays its character recording by Yue Tan; one read another way, or with no character recording (most parts), plays the syllable of the app's pinyin; a neutral-tone one its character recording. (Changed 20 November 2026: before, every single character played its syllable.)

The Lingua Libre recordings are converted from WAV to the same MP3 format, with the silence at the start trimmed (the end kept whole, so soft endings aren't cut) and the loudness evened out.

`tools/build-audio.js` in the app's repository rebuilds the files, so the change can be repeated exactly.
