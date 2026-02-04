# AGENTS.md — flappy-jack

Purpose: quick orientation for contributors and agents.

## Project summary
- Mini web game (One-Tap Tower Stack) built as a single HTML file.
- Designed to run inside a hub iframe and communicate via `postMessage`.
- Includes a standalone hub shim for local testing outside an iframe.

## Key files
- `src/index.html`: game + hub messaging + standalone hub toggle.
- `iframe-integration-spec.md`: parent/iframe message contract and flow.
- `publish/`: build artifacts (`npm pack` output).
- `package.json`: dev scripts and metadata.

## How to run
- `npm start` to serve `src/` locally (uses `http-server`).
- Open the served URL in a browser.

## Iframe integration notes
- Hub sends `HUB_LAUNCH` with `hubOrigin` and `nonce`.
- Game responds with `GAME_READY`, then sends `START_REQUEST` and `END_REQUEST`.
- All outbound messages include the `nonce`.

## Standalone testing
- When opened outside an iframe, a “Standalone Hub” toggle appears.
- Click it to simulate `HUB_LAUNCH` and session lifecycle locally.

## Common edits
- Gameplay tweaks: update logic and UI in `src/index.html`.
- Messaging changes: keep `iframe-integration-spec.md` and `src/index.html` aligned.
