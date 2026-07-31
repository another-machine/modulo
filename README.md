# Modulo

A skinnable step sequencer with a command prompt.

Still very much WIP. Lives at [modulo.amplib.app](https://modulo.amplib.app).
An earlier prototype is at [inst.jake.fun](https://inst.jake.fun), and this is
the next version of [arp.jake.fun](https://arp.jake.fun).

```bash
npm install
npm start        # parcel dev server
npm run build    # static build into dist/
npm run typecheck
```

## Layout

```
src/index.ts          entry point
src/Machine.ts        the machine — owns the clock, mixer, sequencers and keys
src/Sequencer.ts      step sequencing
src/Synths.ts         Tone.js voices
src/Drums.ts          drum voices
src/Renderer.ts       canvas rendering and theming
src/destinations/     the command prompt's addressable tree
src/prompt/           the prompt itself — parsing, interface, ledger
src/style/            css
```

## Packages

This used to live in
[another-machine/public-library](https://github.com/another-machine/public-library)
as `machines/modulo`, importing its siblings by relative source path. It now
consumes them from npm:

| Package                                                                  | Used for                                    |
| ------------------------------------------------------------------------ | ------------------------------------------- |
| [`@amplib/music-theory`](https://www.npmjs.com/package/@amplib/music-theory)     | scales, modes and notes                     |
| [`@amplib/devices`](https://www.npmjs.com/package/@amplib/devices)               | MIDI in and out                             |
| [`@amplib/steganography`](https://www.npmjs.com/package/@amplib/steganography)   | encoding a patch into a shareable image     |

Older, unrelated work that used to sit at this path is at
[ja-k-e/modulo](https://github.com/ja-k-e/modulo).

## Deploy

GitHub Pages, from `.github/workflows/main.yml` on every push to `main`. Parcel
inlines everything into a single `dist/index.html`, so there is no base path to
configure — the `CNAME` written during the build points the artifact at
`modulo.amplib.app`.

`npm run typecheck` is not part of the build. It currently reports 6
pre-existing errors in this repo's own code, none from the packages above.
