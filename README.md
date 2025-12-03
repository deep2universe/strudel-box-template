# Strudel Box Template

A template project for the VS Code extension [Strudel Box](https://marketplace.visualstudio.com/items?itemName=deep2universe.strudel-box) – live-coding music patterns directly in VS Code.

## What is Strudel Box?

Strudel Box is a VS Code extension that integrates the Strudel audio engine (@strudel/web) in a webview-based REPL. You can:

- Program and play music patterns in real-time
- Use synthesizers and sample libraries
- Apply audio effects, scales, and chords
- Choose between different visual themes (Cyberpunk, Halloween, 8-Bit)

## Project Structure

```
/
├── README.md                       # This file
├── STRUDEL_BOX_PATTERN_GUIDE.md    # Complete pattern reference
├── halloween-horror.strudel        # Dark Cinematic Atmosphere (80 BPM)
├── halloween-house.strudel         # Spooky Dancefloor (124 BPM)
├── halloween-piano.strudel         # Haunting Piano Journey (72 BPM)
└── .kiro/
    └── steering/                   # AI steering rules for Kiro
        ├── product.md              # Product overview
        ├── structure.md            # Project structure conventions
        ├── strudel-guide.md        # Strudel syntax guide
        └── tech.md                 # Tech stack documentation
```

## Included Patterns

| File | Genre | BPM | Description |
|------|-------|-----|-------------|
| `halloween-horror.strudel` | Dark Ambient | 80 | Ominous drones, dissonant pads, music box melody |
| `halloween-house.strudel` | House | 124 | Four-on-the-floor with spooky chords |
| `halloween-piano.strudel` | Cinematic | 72 | Chromatic piano phrases, tritones, tremolos |

## Quick Start

1. Install [Strudel Box](https://marketplace.visualstudio.com/items?itemName=deep2universe.strudel-box) in VS Code
2. Open a `.strudel` file
3. Press `Ctrl+Enter` (or `Cmd+Enter` on Mac) to play the pattern
4. Edit the code and hear changes in real-time

## Kiro Steering Documentation

This template includes steering documents for [Kiro](https://kiro.dev) that help AI assistants generate syntactically correct Strudel patterns.

### What are Steering Documents?

Steering documents are Markdown files in the `.kiro/steering/` directory that provide additional context and instructions for AI interactions. They are automatically included in the context.

### Steering Document Structure

| File | Purpose |
|------|---------|
| `product.md` | Describes core features of Strudel Box |
| `structure.md` | Defines project structure and code conventions |
| `strudel-guide.md` | Complete syntax guide with mini-notation, effects, examples |
| `tech.md` | Tech stack, available samples/synths, unsupported features |

### Steering Modes

Steering files can be included in different ways:

```yaml
---
inclusion: always      # Always include (default)
---
```

```yaml
---
inclusion: fileMatch
fileMatchPattern: '*.strudel'   # Only for matching files
---
```

```yaml
---
inclusion: manual      # Only when explicitly referenced with #
---
```

### File References

Steering documents can reference other files:

```markdown
#[[file:openapi.yaml]]
#[[file:schema.graphql]]
```

## Creating Your Own Patterns

```javascript
// Example: Minimal Techno
setcpm(130)

stack(
  s("bd*4"),
  s("~ cp ~ cp"),
  s("hh*8").gain(0.6),
  note("c1").sound("sawtooth").lpf(200)
).gain(0.8)
```

### Best Practices

- Use built-in synths: `sawtooth`, `sine`, `square`, `triangle`
- Standard samples: `bd`, `sd`, `hh`, `cp`, `oh`
- Set BPM explicitly: `setcpm(120)`
- Prevent clipping: `.gain(0.8)` at the end
- Layer with `stack()` for multiple patterns

## License

MIT
