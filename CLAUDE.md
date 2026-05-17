# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file HTML blessing/greeting card generator (`heart.html`, ~1500 lines). No build system, no dependencies beyond CDN fonts. Open directly in a browser.

## Architecture

Everything lives in `heart.html`:

- **CSS (lines ~13-620)**: CSS variables for theming (`--gold`, `--rose`, `--lavender`, `--sakura`), glass-morphism cards, responsive layout, sparkle/trail animations
- **HTML (lines ~620-720)**: Minimal — a canvas overlay, tooltip, language/mood selectors, TTS controls
- **JS (lines ~720-1494)**: All logic in a single IIFE

### Key JS subsystems

| Subsystem | Purpose |
|---|---|
| **Canvas heart particles** | `hearts[]` array, `animH()` RAF loop, `startAnim()`/`stopAnim()` lifecycle |
| **DOM sparkle effects** | `spawnSparkles()` creates lightweight DOM elements with CSS animations |
| **Card generation** | `showBlessing()` renders blessing cards with mood-specific styling |
| **TTS engine** | Web Speech API with per-language `MOOD` config (rate, pitch, pauseMid, pauseEnd) |
| **Recording** | MediaRecorder → WAV fallback via `encodeWav()`, stores in `recordings` Map keyed by card element |
| **Multi-language** | 4 languages (en/zh/ja/de), each with 5 moods (birthday/happy/sad/encouraging/luck) |

### Important patterns

- Cards are DOM elements stored in a `Map` (for recordings) — not virtual DOM
- Animation loop auto-stops when `hearts[]` empties; restarts on next interaction
- `visibilitychange` listener cleans up trails and cancels animation when tab hidden
- TTS uses sentence segmentation (`splitBlessing()`) with per-segment pause scheduling
- Recording playback has blob URL → FileReader data URL fallback chain
- `requestAnimationFrame` defers heavy sparkle rendering after card click for responsiveness

## Development

No build step. Edit `heart.html` and refresh browser. Use browser DevTools for debugging.

## Commit Convention

Use descriptive commit messages. Current history uses sentence-style messages (e.g., "Optimize TTS pauses, fix Chinese recording playback, reduce memory usage").
