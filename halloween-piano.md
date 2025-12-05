# 🎃🎹 Halloween Piano - A Beginner's Guide

Welcome to "Halloween Piano," a haunting, atmospheric piece that creates the feeling of wandering through a spooky mansion at midnight. This tutorial will walk you through every part of the code so you can understand how it works and start creating your own eerie compositions!

## What Does This Pattern Sound Like?

This pattern creates a layered piano composition with eight distinct voices:
- A chromatic descending melody that feels like something creeping down a staircase
- Deep, rumbling bass octaves from the crypt below
- Dissonant chord stabs using tritones (the "devil's interval")
- Ghostly high-register trills that shimmer and pan across the stereo field
- Creeping mid-range arpeggios with echo effects
- Thunderous sub-bass rumbles from the depths
- Ethereal high harmonics like spectral whispers
- A subtle heartbeat pulse building tension

The result is cinematic horror-inspired ambient music at a grave 42 BPM (168 cycles per minute).

---

## Code Breakdown

### Setting the Tempo

```javascript
setcpm(42)
```

`setcpm()` sets the tempo in "cycles per minute." At 42 CPM, each cycle takes about 1.4 seconds — very slow and deliberate, perfect for building dread and suspense.

---

### The `stack()` Function

```javascript
stack(
  // ... all the patterns go here ...
).gain(0.8)
```

`stack()` plays multiple patterns simultaneously, layering them on top of each other. Think of it like tracks in a DAW — each pattern inside `stack()` is a separate instrument or voice playing at the same time.

The `.gain(0.8)` at the very end controls the overall volume (80%) to prevent audio clipping.

---

### Layer 1: Eerie Chromatic Melody

```javascript
note("<[c5 b4 bb4 a4] [ab4 g4 gb4 f4] [e4 eb4 d4 db4] [c4 ~ b3 ~]>")
  .sound("piano")
  .gain(0.7)
  .room(0.6)
  .delay(0.2)
  .delayfeedback(0.4)
```

**What it does:** Creates the primary melody — a chromatic descent that sounds like something slowly creeping down stairs.

**Breaking it down:**
- `note("...")` — Plays musical notes
- `<...>` — Angle brackets alternate between options each cycle, so each phrase plays on a different cycle
- `[c5 b4 bb4 a4]` — Square brackets group notes together within one beat, creating fast runs
- `bb4` — The "b" after a note means flat (half step down)
- `~` — A rest (silence)
- `.sound("piano")` — Uses the piano sound
- `.room(0.6)` — Adds reverb for a spacious, haunted hall feel
- `.delay(0.2)` — Adds echo effect
- `.delayfeedback(0.4)` — Controls how many times the echo repeats

The chromatic descent (moving by half steps) creates an unsettling, horror-movie feel.

---

### Layer 2: Haunting Bass Octaves

```javascript
note("<[c2 c3] [ab1 ab2] [g1 g2] [gb1 gb2]>/2")
  .sound("piano")
  .gain(0.6)
  .attack(0.05)
  .release(1.2)
  .room(0.5)
```

**What it does:** Deep, slow-moving bass octaves that anchor the piece with an ominous foundation.

**New concepts:**
- `[c2 c3]` — Playing two notes an octave apart simultaneously creates a powerful, full bass sound
- `/2` — Slows the pattern to half speed (plays over 2 cycles)
- `.attack(0.05)` — How quickly the note reaches full volume (fast attack = punchy)
- `.release(1.2)` — How long the note fades out after release (long = sustained, eerie)

The bass moves through C, Ab, G, Gb — a descending chromatic pattern that mirrors the melody.

---

### Layer 3: Dissonant Chord Stabs

```javascript
note("<[c4,gb4,b4] ~ [ab3,d4,g4] ~ [g3,db4,f4] ~ [gb3,c4,e4] ~>")
  .sound("piano")
  .gain(0.5)
  .attack(0.01)
  .decay(0.3)
  .sustain(0.2)
  .release(0.8)
  .room(0.7)
  .sometimes(x => x.delay(0.125))
```

**What it does:** Sharp, dissonant chord stabs using tritones — the infamous "devil's interval."

**New concepts:**
- `[c4,gb4,b4]` — Commas inside brackets play notes simultaneously as a chord
- Tritone: The interval between C and Gb (6 semitones) was historically called "diabolus in musica" (the devil in music)
- `.decay(0.3)` — How quickly the note drops from peak to sustain level
- `.sustain(0.2)` — The level the note holds at (low = notes die quickly)
- `.sometimes(x => x.delay(0.125))` — 50% of the time, adds a short delay effect

The `~` rests between chords create a stabbing, jump-scare effect.

---

### Layer 4: Ghostly High Trills

```javascript
note("[c6 db6]*4, [e6 f6]*4, [g6 ab6]*4, [b6 c7]*4")
  .sound("piano")
  .gain(0.35)
  .attack(0.02)
  .release(0.2)
  .room(0.8)
  .pan(sine.range(0.2, 0.8).slow(2))
  .rarely(x => x.fast(2))
```

**What it does:** Rapid trills in the highest register that shimmer and move across the stereo field.

**New concepts:**
- `[c6 db6]*4` — The `*4` repeats the pattern 4 times per beat, creating rapid trills
- `,` — Commas stack patterns to play simultaneously
- `.pan(sine.range(0.2, 0.8).slow(2))` — Automatically pans left-to-right using a sine wave LFO
- `.rarely(x => x.fast(2))` — 25% of the time, doubles the speed for extra chaos

These high trills create an unsettling, shimmering atmosphere like ghostly whispers.

---

### Layer 5: Creeping Arpeggios

```javascript
note("<[c4 eb4 gb4 a4] [ab3 b3 d4 f4] [g3 bb3 db4 e4] [gb3 a3 c4 eb4]>")
  .sound("piano")
  .gain(0.45)
  .attack(0.1)
  .release(0.6)
  .room(0.5)
  .delay(0.33)
  .delayfeedback(0.3)
  .every(4, x => x.rev())
```

**What it does:** Rising arpeggios built on diminished patterns that sound like shadows crawling up walls.

**New concepts:**
- Each arpeggio uses notes that form dissonant, diminished-like patterns
- `.every(4, x => x.rev())` — Every 4 cycles, reverses the pattern (notes play backward)

The combination of delay and reversal creates an unpredictable, creeping sensation.

---

### Layer 6: Thunderous Rumbles

```javascript
note("<c1 ~ ~ ab0 ~ ~ g0 ~ ~ gb0 ~ ~>/3")
  .sound("piano")
  .gain(0.55)
  .attack(0.2)
  .release(2)
  .room(0.9)
  .size(0.95)
  .lpf(400)
```

**What it does:** Extremely low sub-bass notes that rumble like thunder from deep underground.

**New concepts:**
- `c1`, `ab0`, `g0`, `gb0` — Very low octaves (0 and 1) create sub-bass frequencies you feel more than hear
- `/3` — Slows the pattern to 1/3 speed (very slow)
- `.size(0.95)` — Controls reverb size (large = cavernous)
- `.lpf(400)` — Low-pass filter removes high frequencies, keeping only the deep rumble

---

### Layer 7: Spectral Whispers

```javascript
note("<[c7 ~ e7 ~] [~ ab6 ~ b6] [g6 ~ bb6 ~] [~ db7 ~ f6]>")
  .sound("piano")
  .gain(0.25)
  .attack(0.3)
  .release(1.5)
  .room(0.95)
  .hpf(2000)
  .pan(sine.range(0, 1).slow(8))
  .often(x => x.slow(2))
```

**What it does:** Ethereal high harmonics that float like ghostly whispers.

**New concepts:**
- `.hpf(2000)` — High-pass filter removes low frequencies, keeping only the airy highs
- `.pan(sine.range(0, 1).slow(8))` — Very slow panning across the full stereo field
- `.often(x => x.slow(2))` — 75% of the time, plays at half speed for an even more ethereal feel

---

### Layer 8: Heartbeat Pulse

```javascript
s("bd:3 ~ bd:3 ~, ~ ~ ~ cp?")
  .gain(0.3)
  .room(0.6)
  .lpf(300)
```

**What it does:** A subtle, muffled heartbeat with occasional clap accents.

**New concepts:**
- `s("...")` — Uses samples instead of piano notes
- `bd:3` — Bass drum, sample variation 3
- `cp?` — Clap with 50% probability (the `?` makes it random)
- `.lpf(300)` — Heavy low-pass filter makes it sound muffled, like a heartbeat through walls

---

## Quick Reference: Functions Used

| Function | What It Does |
|----------|--------------|
| `setcpm(n)` | Sets tempo (cycles per minute) |
| `stack(...)` | Plays multiple patterns simultaneously |
| `note("...")` | Plays musical notes |
| `s("...")` | Plays samples |
| `.sound("piano")` | Selects the piano sound |
| `.gain(n)` | Volume (0-1) |
| `.room(n)` | Reverb amount (0-1) |
| `.size(n)` | Reverb size |
| `.delay(n)` | Echo timing |
| `.delayfeedback(n)` | Echo repetitions |
| `.attack(n)` | Note fade-in time |
| `.decay(n)` | Time to reach sustain level |
| `.sustain(n)` | Held volume level |
| `.release(n)` | Note fade-out time |
| `.lpf(n)` | Low-pass filter (Hz) |
| `.hpf(n)` | High-pass filter (Hz) |
| `.pan(n)` | Stereo position (0=left, 1=right) |
| `.every(n, fn)` | Apply function every n cycles |
| `.sometimes(fn)` | Apply function 50% of the time |
| `.often(fn)` | Apply function 75% of the time |
| `.rarely(fn)` | Apply function 25% of the time |

---

## Tips for Experimenting

1. **Change the tempo:** Try `setcpm(30)` for an even slower, more dread-filled pace, or `setcpm(60)` for more urgency.

2. **Adjust the dissonance:** The tritone chords use intervals like C-Gb. Try changing `gb4` to `g4` for a less dissonant (but still spooky) sound.

3. **More reverb = more haunted:** Increase `.room(0.95)` on multiple layers for a massive, cathedral-like space.

4. **Add more randomness:** Change `.sometimes()` to `.often()` or add `?` to more notes for unpredictable scares.

5. **Swap the bass notes:** Try changing the bass pattern to `<[d2 d3] [bb1 bb2] [a1 a2] [ab1 ab2]>` for a different harmonic flavor.

6. **Remove layers:** Comment out a layer (add `//` at the start) to hear how each voice contributes to the whole.

7. **Change the filter sweeps:** Try adding `.lpf(sine.range(200, 2000).slow(8))` to the melody for a sweeping, cinematic effect.

8. **Make it scarier:** Add `.speed(-1)` to reverse samples, or `.chop(8).rev()` to create glitchy, unsettling textures.

---

## Musical Techniques Used

- **Chromatic descent:** Moving by half steps creates tension and unease
- **Tritones:** The "devil's interval" (6 semitones) sounds inherently unstable
- **Octave doubling:** Playing the same note in two octaves creates power and depth
- **Sparse rhythms:** Lots of rests (`~`) create suspense and jump-scare moments
- **Extreme registers:** Very high and very low notes feel otherworldly
- **Heavy reverb:** Large spaces sound haunted and mysterious
- **Slow tempo:** Deliberate pacing builds dread

---

## Have Fun!

The beauty of Strudel is how easy it is to experiment. Change a number, swap a note, add an effect — you can't break anything, and happy accidents often lead to the best discoveries. Now go create something that would make a ghost proud! 👻🎹
