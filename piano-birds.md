# 🐦🎹 Piano Birds - A Beginner's Guide

Welcome to "Piano Birds," a gentle, atmospheric piece that creates the feeling of birdsong in a peaceful forest using only piano sounds. This tutorial will walk you through every part of the code so you can understand how it works and start experimenting on your own!

## What Does This Pattern Sound Like?

This pattern creates a layered piano composition with six distinct voices:
- High, chirpy melodies that mimic bird calls
- A deep, grounding bass line (like a wise owl)
- Soft harmonies in the middle register
- Sparkling high notes with echo effects
- A gentle rhythmic pulse underneath it all

The result is dreamy, nature-inspired ambient music at a relaxed 110 BPM.

---

## Code Breakdown

### Setting the Tempo

```javascript
setcpm(110)
```

`setcpm()` sets the tempo in "cycles per minute." At 110 CPM, each cycle (one full loop of your pattern) takes just over half a second. This gives the piece a calm, unhurried feel.

---

### The `stack()` Function

```javascript
stack(
  // ... all the patterns go here ...
).gain(0.8)
```

`stack()` plays multiple patterns at the same time, layering them on top of each other. Think of it like tracks in a DAW — each pattern inside `stack()` is a separate instrument or voice playing simultaneously.

The `.gain(0.8)` at the very end controls the overall volume (80%) to prevent audio clipping.

---

### Layer 1: Main Bird Melody

```javascript
note("[c5 e5 g5 e5] [d5 f5 a5 f5] [e5 g5 b5 g5] [c5 e5 g5 c6]")
  .s("piano")
  .velocity(0.7)
  .room(0.4)
  .gain(0.7)
```

**What it does:** Creates the primary melody — quick, rising arpeggios that sound like bird trills.

**Breaking it down:**
- `note("...")` — Plays musical notes. The numbers (like `c5`, `e5`) indicate pitch, where higher numbers = higher octaves.
- `[c5 e5 g5 e5]` — Square brackets group notes together within one beat. This creates fast runs of four notes.
- `.s("piano")` — Uses the piano sound.
- `.velocity(0.7)` — How hard the keys are "pressed" (0-1). Higher = louder and brighter.
- `.room(0.4)` — Adds reverb (echo/space). 0.4 is a moderate amount.
- `.gain(0.7)` — Volume for this specific layer.

---

### Layer 2: Answering Bird Call

```javascript
note("~ [g5 a5 g5] ~ [e5 f5 e5]")
  .s("piano")
  .velocity(0.6)
  .delay(0.15)
  .gain(0.6)
```

**What it does:** A second bird "responds" to the first with shorter phrases and silences between them.

**New concepts:**
- `~` — A rest (silence). This creates space in the pattern.
- `.delay(0.15)` — Adds an echo effect. The 0.15 controls how quickly the echo repeats.

The pattern plays: silence, three quick notes, silence, three quick notes — like a bird calling back!

---

### Layer 3: Gentle Bass (The Wise Owl)

```javascript
note("<c2 g2> <e2 b2> <a2 e2> <g2 d2>")
  .s("piano")
  .velocity(0.5)
  .room(0.3)
  .gain(0.6)
```

**What it does:** Deep, slow-moving bass notes that anchor the piece.

**New concept:**
- `<...>` — Angle brackets alternate between options each cycle. So `<c2 g2>` plays C2 on the first cycle, G2 on the second, then repeats.

The `2` in `c2` means octave 2 — very low notes that give the piece warmth and depth.

---

### Layer 4: Mid-Range Harmony (Rustling Feathers)

```javascript
note("<[c3 e3 g3] [d3 f3 a3] [e3 g3 b3] [c3 e3 g3]>")
  .s("piano")
  .velocity(0.4)
  .room(0.5)
  .gain(0.5)
```

**What it does:** Soft chords in the middle register that fill out the harmony.

**Combining concepts:**
- The `<...>` means each chord plays on a different cycle
- The `[...]` groups three notes to play as a quick chord/arpeggio
- These are triads (three-note chords): C major, D minor, E minor, C major

---

### Layer 5: Sparkling High Notes (Morning Dew)

```javascript
note("~ ~ [c6 e6] ~ ~ ~ [g5 b5] ~")
  .s("piano")
  .velocity(0.5)
  .delay(0.2)
  .delayfeedback(0.3)
  .room(0.6)
  .gain(0.4)
```

**What it does:** Occasional high sparkles with lots of echo — like light glinting off dewdrops.

**New concept:**
- `.delayfeedback(0.3)` — Controls how many times the echo repeats. Higher values = longer, more pronounced echoes.

Notice all the rests (`~`) — this layer is mostly silence with occasional bright notes, creating a sense of space.

---

### Layer 6: Rhythmic Pulse (Forest Heartbeat)

```javascript
note("[c4 ~ e4 ~]*2")
  .s("piano")
  .velocity(0.3)
  .gain(0.4)
```

**What it does:** A subtle, steady pulse that gives the piece gentle momentum.

**New concept:**
- `*2` — Repeats the pattern twice per cycle. So `[c4 ~ e4 ~]*2` plays: C4, rest, E4, rest, C4, rest, E4, rest.

The low velocity (0.3) keeps this very soft — you feel it more than hear it.

---

## Quick Reference: Functions Used

| Function | What It Does |
|----------|--------------|
| `setcpm(n)` | Sets tempo (cycles per minute) |
| `stack(...)` | Plays multiple patterns simultaneously |
| `note("...")` | Plays musical notes |
| `.s("piano")` | Selects the piano sound |
| `.velocity(n)` | Key pressure/brightness (0-1) |
| `.room(n)` | Reverb amount (0-1) |
| `.delay(n)` | Echo timing |
| `.delayfeedback(n)` | Echo repetitions |
| `.gain(n)` | Volume (0-1) |

---

## Tips for Experimenting

1. **Change the tempo:** Try `setcpm(80)` for a slower, dreamier feel, or `setcpm(140)` for more energy.

2. **Swap instruments:** Replace `.s("piano")` with `.s("sawtooth")` or `.s("sine")` for a synth version.

3. **Adjust the reverb:** Increase `.room(0.8)` for a more spacious, cathedral-like sound.

4. **Add more delay:** Try `.delayfeedback(0.6)` on the sparkling notes for longer, more ethereal echoes.

5. **Change the notes:** The melody uses C major patterns. Try changing `c5` to `c#5` or `d5` to shift the mood.

6. **Remove layers:** Comment out a layer (add `//` at the start) to hear how each voice contributes to the whole.

7. **Add randomness:** Try adding `?` after notes like `"c5? e5 g5? e5"` — the `?` gives each note a 50% chance of playing.

---

## Have Fun!

The beauty of Strudel is how easy it is to experiment. Change a number, swap a note, add an effect — you can't break anything, and happy accidents often lead to the best discoveries. 🐦✨
