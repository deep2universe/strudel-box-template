# Project Structure

This repository contains documentation and pattern guides for the Strudel Box VS Code extension.

## Files
```
/
├── STRUDEL_BOX_PATTERN_GUIDE.md   # Complete pattern reference for AI assistants
└── .kiro/
    └── steering/                   # AI steering rules
```

## Pattern Guide Organization
The main guide (`STRUDEL_BOX_PATTERN_GUIDE.md`) covers:
1. Basic syntax and mini-notation
2. Sound sources (synths and samples)
3. Audio effects
4. Pattern modification
5. Scales and chords
6. Complete examples by genre
7. Best practices for AI-generated patterns

## Code Conventions for .strudel Files
- Use dot-chaining for modifications
- Prefer built-in synths (`sawtooth`, `sine`, `square`, `triangle`) for reliability
- Use standard samples (`bd`, `sd`, `hh`, `cp`) that are always loaded
- End patterns with `.gain(0.8)` to prevent clipping
- Use `setcpm(120)` for explicit tempo
- Use `stack()` for layering multiple patterns
- Patterns are synchronous - no async/await
