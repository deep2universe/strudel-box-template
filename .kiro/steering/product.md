---
inclusion: always
---

# Strudel Box Product Guide

VS Code extension for live-coding music patterns using the Strudel audio engine (@strudel/web).

## File Format
- Extension: `.strudel`
- Syntax: JavaScript (ES2020+)
- Patterns are synchronous — no async/await

## Available Sound Sources
- Synthesizers: `sawtooth`, `square`, `triangle`, `sine` (always available)
- Sample libraries: tidal-drum-machines, piano, Dirt-Samples, EmuSP12, vcsl
- Standard samples: `bd`, `sd`, `hh`, `cp`, `oh`, `cb`

## Code Style Requirements
- Use dot-chaining for modifications (e.g., `.lpf(800).room(0.3).gain(0.8)`)
- End patterns with `.gain(0.8)` to prevent clipping
- Set tempo explicitly with `setcpm(120)`
- Use `stack()` for layering multiple patterns
- Prefer built-in synths over samples for reliability

## Strudel Player - Open in Browser
- The extension includes a "Strudel Player" feature that opens `.strudel` files directly on strudel.cc
- Use this to access the full Strudel web environment with additional features
- Hydra Visuals and other web-only features are available when opened via strudel.cc

## Not Supported (in VS Code extension)
- CSound, Tidal syntax
- External/custom samples
- Async operations
- Hydra Visuals (use Strudel Player to open in browser for visualizations)
