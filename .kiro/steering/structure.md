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

## AI File Creation Rules
When creating Strudel patterns, the AI must:
1. **Always create new files** - Do not output patterns inline, always save to a `.strudel` file
2. **Check for existing files** - Before creating a new file, verify if a file with the same name already exists
3. **Use `.strudel` extension** - All pattern files must end with `.strudel`
4. **Default location is root** - Save files to the workspace root directory unless otherwise specified
5. **Use descriptive names** - Name files based on their content (e.g., `techno-beat.strudel`, `ambient-pad.strudel`)
