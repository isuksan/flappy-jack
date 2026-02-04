# flappy-jack

Flappy Jack web game and iframe integration assets.

## Overview
- Single-file HTML5 game (canvas) with HUD + overlays.
- Intended to run inside a Mini Game Hub iframe using `postMessage`.
- Includes a standalone hub shim to test gameplay without an iframe.

## File structure

```
.
├── AGENTS.md
├── README.md
├── iframe-integration-spec.md
├── package.json
├── publish/
└── src/
    └── index.html
```

## Getting started

- `npm start` serves `src/` via `http-server`.
- `npm pack` creates a tarball in `publish/`.

## Iframe integration (game-side)

- Hub sends `HUB_LAUNCH` with `hubOrigin` + `nonce`.
- Game replies with `GAME_READY` and sends `START_REQUEST` when play begins.
- Game sends `END_REQUEST` once per run with score + elapsed time.
- All outbound messages must include the `nonce`.

## Standalone testing

When opened outside an iframe, a “Standalone Hub” toggle appears in the bottom-right.
Click it to simulate `HUB_LAUNCH` and the session lifecycle locally.

## More details

See `AGENTS.md` for a quick contributor overview and `iframe-integration-spec.md` for the full message contract.
