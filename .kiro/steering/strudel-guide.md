# Strudel Box - AI Guide for Music Patterns

> This guide enables AI assistants to generate syntactically correct and functional Strudel patterns for the VS Code extension "Strudel Box".

## Basics

**File format:** `.strudel` | **Syntax:** JavaScript (ES2020+)

### Pattern Entry Points
```javascript
s("bd sd hh cp")           // Sample-based
sound("bd sd hh cp")       // Alternative
note("c3 e3 g3 c4")        // Note-based
n("0 2 4 7")               // Number-based
```

### Mini-Notation
| Symbol | Meaning | Example |
|--------|---------|---------|
| ` ` | Sequence | `"bd sd hh"` |
| `*n` | Repetition | `"hh*4"` → 4x hh |
| `/n` | Slow down | `"bd/2"` → every 2 cycles |
| `[...]` | Grouping | `"[bd sd] hh"` |
| `<...>` | Alternation | `"<bd sd>"` |
| `,` | Parallel/Stack | `"bd, hh*4"` |
| `~` | Rest | `"bd ~ sd ~"` |
| `:n` | Sample index | `"bd:2"` |
| `?` | Random (50%) | `"hh?"` |

---

## Sound Sources

### Synthesizers (always available)
```javascript
.sound("sawtooth")   // Sawtooth wave
.sound("square")     // Square wave
.sound("triangle")   // Triangle wave
.sound("sine")       // Sine wave
```

### Sample Libraries (pre-loaded)
| Library | Description |
|---------|-------------|
| `tidal-drum-machines` | Roland TR-808, TR-909, TR-707 |
| `piano` | Acoustic piano |
| `Dirt-Samples` | Classic TidalCycles samples |
| `EmuSP12` | Legendary sampler |
| `vcsl` | Versilian Community Sample Library |

### Standard Samples
```javascript
// Drums
s("bd")   // Bass Drum    s("sd")   // Snare
s("hh")   // Hi-Hat       s("oh")   // Open Hi-Hat
s("cp")   // Clap         s("cb")   // Cowbell

// Instruments
s("piano")  s("casio")  s("gtr")  s("bass")  s("arpy")  s("pluck")

// Drum Machines
s("bd sd hh cp").bank("RolandTR909")
s("bd sd hh cp").bank("RolandTR808")
```

---

## Audio Effects

### Filters
```javascript
.lpf(800)           // Low-pass filter (Hz)
.hpf(200)           // High-pass filter
.lpq(5)             // Resonance
.lpf(sine.range(200, 2000).slow(4))  // LFO-modulated
```

### Space & Delay
```javascript
.room(0.5)          // Reverb (0-1)
.size(0.8)          // Reverb size
.delay(0.25)        // Delay time
.delayfeedback(0.5) // Delay feedback
```

### Amplitude & Envelope
```javascript
.gain(0.8)          // Volume
.attack(0.1)        // Attack
.decay(0.2)         // Decay
.sustain(0.5)       // Sustain
.release(0.3)       // Release
.pan(0.5)           // Panning (0=left, 1=right)
```

---

## Pattern Modification

### Timing
```javascript
.fast(2)            // Double speed
.slow(2)            // Half speed
```

### Structure
```javascript
.rev()              // Reverse
.palindrome()       // Forward and backward
.iter(4)            // Rotate through 4 versions
```

### Combination
```javascript
stack(s("bd*4"), s("hh*8"), note("c3").sound("sine"))  // Parallel
cat(s("bd*4"), s("sd*4"))                              // Sequential
```

### Euclidean Rhythms
```javascript
.euclid(3, 8)       // 3 hits over 8 steps
.euclid(5, 8, 2)    // With rotation
```

### Conditional Modification
```javascript
.sometimes(x => x.fast(2))   // 50% probability
.often(x => x.rev())         // 75%
.rarely(x => x.speed(-1))    // 25%
.every(4, x => x.fast(2))    // Every 4 cycles
```

---

## Scales & Chords

### Scales
```javascript
.scale("C:major")      .scale("C:minor")
.scale("C:dorian")     .scale("C:phrygian")
.scale("C:pentatonic") .scale("C:blues")
```

### Chords
```javascript
chord("<C Am Dm G>")           // Progression
chord("<C^7 Am7 Dm7 G7>")      // With 7ths
.voicing()                      // Apply voicing
```

---

## Tempo
```javascript
setcpm(120)         // 120 BPM
setCps(2)           // 2 cycles/second = 120 BPM
```

---

## Genre Examples

**Techno (130 BPM):**
```javascript
setcpm(130)
stack(
  s("bd*4"),
  s("~ cp ~ cp"),
  s("hh*8").gain(0.6),
  note("c1").sound("sawtooth").lpf(200)
).gain(0.8)
```

**House (124 BPM):**
```javascript
setcpm(124)
stack(
  s("bd*4, hh*8"),
  s("~ cp ~ cp"),
  chord("<Cm7 Fm7>").voicing().sound("piano").room(0.4)
).gain(0.8)
```

**Ambient (60 BPM):**
```javascript
setcpm(60)
stack(
  note("c3 e3 g3 b3").sound("sine").attack(2).release(4).room(0.9).gain(0.4),
  s("bd ~ ~ ~").room(0.8).gain(0.3)
).gain(0.8)
```

---

## Best Practices

1. **Prefer synthesizers** - `sawtooth`, `sine`, `square`, `triangle` are always available
2. **Use standard samples** - `bd`, `sd`, `hh`, `cp` are reliably loaded
3. **Control gain** - `.gain(0.8)` at the end prevents clipping
4. **Use room sparingly** - `.room(0.2-0.4)` for subtle space
5. **Set BPM explicitly** - `setcpm(120)` for clear tempo indication
6. **Use stack() for layering** - Multiple simultaneous patterns
7. **No async/await** - Strudel patterns are synchronous
8. **No external samples** - Only use pre-loaded libraries

---

## Not Available

- CSound (`loadCsound`, `.csound()`)
- Hydra Visuals (`initHydra`, `osc()`)
- Tidal Syntax (`tidal\`d1 $ s "bd"\``)
