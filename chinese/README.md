# Chinese stroke data

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
