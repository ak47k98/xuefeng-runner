# xuefeng-runner

Static website: Chrome T-Rex runner game with custom BGM and character reskin. No build system, no package manager, no tests.

## Structure

- `index.html` — entry point, loads `index.js` and `index.css`, contains base64-encoded sound FX in `<template>` tag
- `index.js` — all game logic in a single IIFE, vanilla JS, no modules/imports
- `index.css` — game styles
- `assets/default_200_percent/` — sprite sheets and error icon (2x only, `IS_HIDPI` is hardcoded `true`)
- `assets/music/bgm.mp3` — background music, looped via `<audio id="bgm-audio">`

## Key Quirks

- `IS_HIDPI` is forced `true` at `index.js:95` — always uses 2x sprite sheet; do not restore dynamic detection
- `IS_IOS` disables Web Audio sound FX entirely (`index.js:318`), BGM still plays via `<audio>` element
- Game auto-enters "arcade mode" (fullscreen scaling) on first jump via `setArcadeMode()`
- BGM volume hardcoded to 0.3 at `index.js:920`
- Sprite coordinates in `Runner.spriteDefinition` must match the sprite sheet PNGs exactly

## How to Run

Open `index.html` in a browser. For local dev, any static file server works:
```
python3 -m http.server 8000
```

## Deployment

GitHub Pages at `https://hychyssan.github.io/xuefeng-runner/` — served directly from repo root.
