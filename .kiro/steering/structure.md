---
inclusion: fileMatch
fileMatchPattern: '**/*.strudel'
---

# Strudel Pattern File Conventions

## File Creation Rules
- Always save patterns to `.strudel` files in the workspace root
- Check for existing files before creating new ones
- Use descriptive, kebab-case names (e.g., `techno-beat.strudel`, `ambient-pad.strudel`)
- Never output patterns inline — always write to a file

## Code Style
- Dot-chain all modifications: `.lpf(800).room(0.3).gain(0.8)`
- End every pattern with `.gain(0.8)` to prevent clipping
- Set tempo explicitly: `setcpm(120)`
- Layer patterns with `stack()`
- No async/await — patterns are synchronous

## Sound Source Priority
1. Built-in synths: `sawtooth`, `sine`, `square`, `triangle` (always available)
2. Standard samples: `bd`, `sd`, `hh`, `cp`, `oh`, `cb` (reliably loaded)
3. Bank samples: `.bank("RolandTR808")`, `.bank("RolandTR909")`

## Reference
See `STRUDEL_BOX_PATTERN_GUIDE.md` for complete syntax, effects, scales, and genre examples.
