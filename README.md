# lifx-tile-fonts

Fonts for use in [LIFX Tile](https://www.lifx.com/collections/creative-tiles) effects. 👨‍🔬🔠

## Requirements

- [`node -v`](https://nodejs.org/en/download/current/) >= `v12.10.*`
- [`npm -v`](https://www.npmjs.com/get-npm) >= `6.10.*`

## Installation

```console
$ npm install furey/lifx-tile-fonts#semver:^v1
```

## Usage

```JavaScript
const { chars, groups } = require('lifx-tile-fonts')
const e = Object.entries

console.log(chars)
// !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[]^|~•

console.log(e(groups).map(([group]) => group))
// [ 'echolevel', 'oldschool-pc-fonts' ]

console.log(e(groups['oldschool-pc-fonts'].fonts).map(([font]) => font))
// [
//   'ami',         'amstrad',
//   'ati',         'dtk',
//   'ibm-bios',    'ibm-cga',
//   'ibm-conv',    'itt',
//   'kaypro2K',    'phoenix-bios',
//   'phoenix-ega', 'tandy-new',
//   'tandy-old',   'toshiba',
//   'verite',      'v-tech'
// ]

const preview = (groupName, fontName, charSymbol) => {
  const group = groups[groupName]
  const font = group.fonts[fontName]
  const char = font.chars[chars.indexOf(charSymbol)]
  console.log(`Group: ${groupName}`)
  console.log(`Font: ${fontName}`)
  console.log(`Char: ${charSymbol}`)
  console.log('Char Bounds:', char.bounds)
  for (let i = 0; i < char.colors.length; i += 8) {
    const row = char.colors.slice(i, i + 8)
    console.log(row.map(_ => _ === 'X' ? '█' : '·').join(''))
  }
}

preview('oldschool-pc-fonts', 'ami', 'A')
// Group: oldschool-pc-fonts
// Font: ami
// Char: A
// Char Bounds: { left: 0, right: 6, top: 1, bottom: 7, width: 7, height: 7 }
// ········
// ··███···
// ·██·██··
// ██···██·
// ██···██·
// ███████·
// ██···██·
// ██···██·

preview('oldschool-pc-fonts', 'ibm-conv', 'A')
// Group: oldschool-pc-fonts
// Font: ibm-conv
// Char: A
// Char Bounds: { left: 1, right: 7, top: 1, bottom: 7, width: 7, height: 7 }
// ········
// ···███··
// ····██··
// ···███··
// ···█·██·
// ··█████·
// ··█···██
// ·██···██

preview('oldschool-pc-fonts', 'v-tech', 'A')
// Group: oldschool-pc-fonts
// Font: v-tech
// Char: A
// Char Bounds: { left: 0, right: 5, top: 1, bottom: 7, width: 6, height: 7 }
// ········
// ··██····
// ·█··█···
// █····█··
// █····█··
// ██████··
// █····█··
// █····█··
```

## Fonts

This repo includes `8x8` fonts sourced from:

- [Protracker v2.3D/v2.3E Font](https://github.com/echolevel/protracker-font)
- [The Ultimate Oldschool PC Font Pack](https://int10h.org/oldschool-pc-fonts/)

## License

ISC License

Copyright (c) 2019, James Furey

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
