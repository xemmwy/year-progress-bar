# Year Progress Bar

How much of the year is gone, as a quiet pastel-pink bar.

The solid fill dissolves at its edge into a dithered pixel grid. Pixels near the fill fade softly on and off; further out they sit still. The dithering never changes the reading: on average the bar covers exactly the share of the year that has passed.

## Use it

Open `index.html` in any browser. No install, no build — one file.

| Action | Does |
|---|---|
| Click the bar · `R` · `Enter`/`Space` on the bar | Replay the fill animation |
| `P` | Pause / resume the flicker |

It follows your system's light/dark setting and turns the motion off when "reduce motion" is on. The value updates every minute, in your local time zone.

## Tweak it

The constants at the top of the script control the look:

| Constant | Default | Meaning |
|---|---|---|
| `PIXEL` | `4` | size of one dither pixel (px) |
| `BAND` | `0.22` | width of the dissolving edge, as a share of the bar |
| `SOFT` | `0.18` | how gently pixels fade (0 = hard blink) |
| `RATE` | `0.22` | blinks per second |
| `FLOW` | `0.045` | how strongly blinks ripple left to right |
| `STILL` | `0.7` | point across the edge where motion stops |
| `FILL_MS` | `1600` | length of the fill animation (ms) |

Colours are CSS variables in `:root` (`--fill` is the pink, `#f6b3c6`).

## How it works

The bar is a canvas with one canvas pixel per 4 px cell, scaled up crisply. Across the edge band, each cell's fill threshold comes from an 8×8 Bayer matrix and sweeps up and down on a slow triangle wave, so cells fade in and out while the band's average density stays fixed. Each cell keeps its own phase, so pausing and resuming never jumps.

## Credits

- Type: [Geist Pixel](https://vercel.com/font) by Vercel (SIL Open Font License), loaded from jsDelivr. Offline it falls back to your monospace font.

## License

[MIT](LICENSE)
