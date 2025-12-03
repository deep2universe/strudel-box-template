---
inclusion: fileMatch
fileMatchPattern: '**/*.strudel'
---

# Strudel Pattern Syntax Guide

Generate syntactically correct Strudel patterns for the VS Code "Strudel Box" extension.

## Core Rules

- File extension: `.strudel`
- Syntax: JavaScript (ES2020+), synchronous only (no async/await)
- Always end patterns with `.gain(0.8)` to prevent clipping
- Always set tempo explicitly with `setcpm(BPM)`
- Use `stack()` for layering multiple patterns
- Prefer built-in synths over samples for reliability

## Pattern Entry Points

```javascript
s("bd sd hh cp")        // Sample-based (preferred)
sound("bd sd hh cp")    // Alternative
note("c3 e3 g3 c4")     // Note-based
n("0 2 4 7")            // Number-based
```

## Mini-Notation Reference

| Symbol | Meaning | Example |
|--------|---------|---------|
| ` ` | Sequence | `"bd sd hh"` |
| `*n` | Repeat n times | `"hh*4"` |
| `/n` | Slow by n | `"bd/2"` |
| `[...]` | Group | `"[bd sd] hh"` |
| `<...>` | Alternate per cycle | `"<bd sd>"` |
| `,` | Stack/parallel | `"bd, hh*4"` |
| `~` | Rest | `"bd ~ sd ~"` |
| `:n` | Sample index | `"bd:2"` |
| `?` | 50% random | `"hh?"` |

## Sound Sources

### Synthesizers (always available)
`sawtooth`, `square`, `triangle`, `sine`

### Standard Samples (reliable)
- Drums: `bd`, `sd`, `hh`, `oh`, `cp`, `cb`
- Instruments: `piano`, `casio`, `gtr`, `bass`, `arpy`, `pluck`

### Drum Machine Banks
```javascript
s("bd sd hh cp").bank("RolandTR808")
s("bd sd hh cp").bank("RolandTR909")
```

## Effects Chain

```javascript
// Filters
.lpf(800).hpf(200).lpq(5)

// Space
.room(0.3).size(0.5).delay(0.25).delayfeedback(0.4)

// Envelope
.attack(0.1).decay(0.2).sustain(0.5).release(0.3)

// Output
.gain(0.8).pan(0.5)
```

## Pattern Modifiers

```javascript
.fast(2)                        // Double speed
.slow(2)                        // Half speed
.rev()                          // Reverse
.euclid(3, 8)                   // Euclidean rhythm
.every(4, x => x.fast(2))       // Every 4 cycles
.sometimes(x => x.rev())        // 50% probability
```

## Combining Patterns

```javascript
stack(pattern1, pattern2, ...)  // Play simultaneously
cat(pattern1, pattern2, ...)    // Play sequentially
```

## Scales & Chords

```javascript
note("0 2 4 7").scale("C:minor")
chord("<C Am Dm G>").voicing().sound("piano")
```

## Template Structure

```javascript
setcpm(120)
stack(
  s("bd*4"),
  s("~ cp ~ cp"),
  s("hh*8").gain(0.6),
  note("c2 c3").sound("sawtooth").lpf(400)
).gain(0.8)
```

## Not Supported

- CSound, Hydra Visuals, Tidal syntax
- External/custom samples
- Async operations
