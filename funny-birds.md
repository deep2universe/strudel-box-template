# 🐦 Funny Birds - A Beginner's Tutorial

Welcome to this playful Strudel pattern! This tutorial will walk you through a whimsical musical piece that brings a whole aviary of silly birds to life through code.

## What Does This Pattern Sound Like?

"Funny Birds" is a lighthearted, comedic piece at 125 BPM that layers seven different musical elements, each representing a different bird character:

- High-pitched chirping melodies
- A waddling bass line (penguin!)
- Rapid pecking rhythms (woodpecker)
- Wobbly flapping sounds
- Honking goose interjections
- A funky chicken drum beat
- Deep owl hoots in the background

The result is organized chaos — a musical comedy sketch performed by feathered friends!

---

## Code Breakdown

### Setting the Tempo

```javascript
setcpm(125)
```

`setcpm()` sets the tempo in **cycles per minute**. At 125 CPM, we get an upbeat, bouncy feel perfect for our silly birds.

---

### The `stack()` Function

```javascript
stack(
  // ... all our bird patterns ...
).gain(0.8)
```

`stack()` is one of the most important functions in Strudel. It plays multiple patterns **simultaneously** — like having all our birds perform together. The final `.gain(0.8)` at the end reduces the overall volume to prevent audio clipping.

---

### 1. Silly Bird Calls (High Chirps)

```javascript
note("c6 e6 g6 c7 ~ e6 c6 ~")
  .s("triangle")
  .decay(0.1)
  .sustain(0)
  .delay(0.2)
  .gain(0.5)
```

**What's happening:**
- `note("c6 e6 g6 c7 ~ e6 c6 ~")` — Plays a sequence of high notes. The `~` symbols are **rests** (silence).
- `.s("triangle")` — Uses the triangle wave synthesizer, which has a soft, flute-like quality.
- `.decay(0.1)` — The sound fades out quickly (0.1 seconds).
- `.sustain(0)` — No sustained tone, making it very "plucky."
- `.delay(0.2)` — Adds a subtle echo effect.
- `.gain(0.5)` — Sets this layer to 50% volume.

**Try this:** Change `c6 e6 g6 c7` to `c7 e7 g7 c8` for even higher, squeakier birds!

---

### 2. Waddling Penguin Bass

```javascript
note("c2 ~ c2 c2 ~ c2 ~ c2")
  .s("sawtooth")
  .lpf(400)
  .decay(0.2)
  .sustain(0.1)
  .gain(0.6)
```

**What's happening:**
- `note("c2 ~ c2 c2 ~ c2 ~ c2")` — Low C notes with rests, creating a "waddle" rhythm.
- `.s("sawtooth")` — Sawtooth waves are buzzy and great for bass.
- `.lpf(400)` — **Low-pass filter** at 400 Hz removes harsh high frequencies, making it warm and rumbly.
- `.decay(0.2)` and `.sustain(0.1)` — Short, punchy notes.

**Try this:** Change `c2` to `c1` for an even deeper, more comical waddle!

---

### 3. Pecking Woodpecker Rhythm

```javascript
s("hh*8")
  .gain("[0.8 0.4 0.6 0.4]*2")
  .pan(sine.range(0.3, 0.7))
```

**What's happening:**
- `s("hh*8")` — Plays the hi-hat sample 8 times per cycle. The `*8` is the **repeat** operator.
- `.gain("[0.8 0.4 0.6 0.4]*2")` — Varies the volume in a pattern, creating an accent rhythm.
- `.pan(sine.range(0.3, 0.7))` — The sound moves left-to-right using a sine wave, like a woodpecker hopping around!

**Try this:** Change `hh*8` to `hh*16` for faster pecking!

---

### 4. Flapping Wings (Wobbly Synth)

```javascript
note("<c4 e4 g4 e4>")
  .s("square")
  .lpf(sine.range(300, 1200).slow(2))
  .decay(0.3)
  .sustain(0.1)
  .room(0.4)
  .gain(0.4)
```

**What's happening:**
- `note("<c4 e4 g4 e4>")` — The `<...>` brackets mean **alternate** — each cycle plays the next note in the sequence.
- `.s("square")` — Square waves have a hollow, buzzy tone.
- `.lpf(sine.range(300, 1200).slow(2))` — The filter sweeps between 300-1200 Hz using a slow sine wave, creating a "wah-wah" wobble effect!
- `.room(0.4)` — Adds reverb (room ambience).

**Try this:** Change `.slow(2)` to `.slow(1)` for faster wobbling!

---

### 5. Angry Goose Honks

```javascript
note("[~ ~ g3 ~]*2")
  .s("sawtooth")
  .lpf(600)
  .decay(0.4)
  .sustain(0.2)
  .gain(0.5)
```

**What's happening:**
- `note("[~ ~ g3 ~]*2")` — The `[...]` groups four events, with the note only on beat 3. The `*2` repeats this twice per cycle.
- The sawtooth wave with a low-pass filter creates a nasal, honk-like sound.

**Try this:** Change `g3` to `a3` or `f3` for different honk pitches!

---

### 6. Funky Chicken Strut Beat

```javascript
s("bd ~ sd:3 bd ~ sd:3 bd cp")
  .gain(0.7)
```

**What's happening:**
- `s()` plays **samples** (pre-recorded sounds).
- `bd` = bass drum, `sd` = snare drum, `cp` = clap.
- `sd:3` — The `:3` selects the 4th variation (index 3) of the snare sample.
- The rhythm has a funky, strutting feel!

**Try this:** Add `.bank("RolandTR808")` to use classic 808 drum sounds!

---

### 7. Owl Hoots

```javascript
note("<[~ ~ ~ c3] [~ ~ ~ g2]>")
  .s("sine")
  .decay(0.5)
  .sustain(0.3)
  .room(0.6)
  .gain(0.4)
```

**What's happening:**
- The pattern alternates between two phrases, each with a note at the end (beat 4).
- `.s("sine")` — Sine waves are pure and smooth, perfect for owl hoots.
- `.room(0.6)` — More reverb makes it sound distant and atmospheric.

**Try this:** Change `c3` and `g2` to `e3` and `b2` for a spookier owl!

---

## Key Concepts Summary

| Function | What It Does |
|----------|--------------|
| `setcpm(125)` | Sets tempo (cycles per minute) |
| `stack()` | Plays multiple patterns at once |
| `note()` | Plays musical notes |
| `s()` / `sound()` | Plays samples |
| `.gain()` | Controls volume (0-1) |
| `.lpf()` | Low-pass filter (removes highs) |
| `.decay()` | How fast sound fades |
| `.sustain()` | How long sound holds |
| `.room()` | Adds reverb |
| `.delay()` | Adds echo |
| `.pan()` | Left/right positioning |
| `~` | Rest (silence) |
| `*n` | Repeat n times |
| `<...>` | Alternate each cycle |
| `[...]` | Group events together |

---

## Experiments to Try

1. **Change the tempo:** Try `setcpm(80)` for a sleepy aviary or `setcpm(160)` for hyperactive birds!

2. **Add a new bird:** Create your own pattern and add it to the stack:
   ```javascript
   // Tweeting sparrow
   note("e5 g5 e5 ~").s("sine").decay(0.05).gain(0.4)
   ```

3. **Remove a bird:** Comment out any section with `//` to hear the mix without it.

4. **Change synths:** Swap `triangle` for `sine`, or `sawtooth` for `square` to hear different timbres.

5. **Add effects:** Try adding `.hpf(200)` (high-pass filter) or `.delayfeedback(0.5)` to any pattern.

Have fun making your own musical menagerie! 🐧🦆🦉
