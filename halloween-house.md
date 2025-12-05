# 🎃🏚️ Halloween House - A Beginner's Guide

Welcome to "Halloween House," a spooky dancefloor track that combines the driving energy of house music with eerie, haunted-mansion vibes. This tutorial will walk you through every part of the code so you can understand how it works and start creating your own spooky bangers!

## What Does This Pattern Sound Like?

This pattern creates a layered house track with nine distinct elements:
- A pounding four-on-the-floor kick drum
- Offbeat hi-hats with random ghost notes
- Classic house claps on beats 2 and 4
- Eerie minor chord stabs using dissonant intervals
- A creeping chromatic bass line that descends into darkness
- Spooky arpeggios built on diminished patterns
- A ghostly evolving pad texture
- Witch-like percussion hits with pitch shifting
- A deep sub-bass pulse you feel more than hear
- Shimmering ride cymbals for drive

The result is dancefloor-ready house music at 128 BPM with a haunted twist.

---

## Code Breakdown

### Setting the Tempo

```javascript
setcpm(32)
```

`setcpm()` sets the tempo in "cycles per minute." In Strudel, 1 cycle = 4 beats, so 32 CPM × 4 = 128 BPM — classic house tempo. This gives the track that driving, danceable energy.

---

### The `stack()` Function

```javascript
stack(
  // ... all the patterns go here ...
).gain(0.8)
```

`stack()` plays multiple patterns simultaneously, layering them on top of each other. Think of it like tracks in a DAW — each pattern inside `stack()` is a separate instrument playing at the same time.

The `.gain(0.8)` at the very end controls the overall volume (80%) to prevent audio clipping.

---

### Layer 1: Four-on-the-Floor Kick

```javascript
s("bd*4")
  .gain(0.85)
  .lpf(800)
```

**What it does:** The foundation of house music — a kick drum on every beat.

**Breaking it down:**
- `s("bd*4")` — Plays the bass drum sample 4 times per cycle (once per beat)
- `*4` — The asterisk repeats the pattern 4 times
- `.gain(0.85)` — Volume at 85% (kicks should be prominent)
- `.lpf(800)` — Low-pass filter at 800Hz removes harsh high frequencies, keeping the kick punchy but not clicky

---

### Layer 2: Offbeat Hi-Hats with Ghost Notes

```javascript
s("~ hh ~ hh, hh*8?")
  .gain(0.55)
  .hpf(6000)
  .pan(sine.range(0.3, 0.7).fast(2))
```

**What it does:** Creates the classic house hi-hat pattern with random ghost notes.

**Breaking it down:**
- `~ hh ~ hh` — Hi-hats on the offbeats (the "and" of each beat). The `~` is a rest (silence).
- `,` — The comma stacks another pattern on top
- `hh*8?` — 8 hi-hats per cycle, but the `?` gives each a 50% chance of playing (ghost notes!)
- `.hpf(6000)` — High-pass filter removes low frequencies, keeping hi-hats crisp
- `.pan(sine.range(0.3, 0.7).fast(2))` — Automatically pans left-to-right using a sine wave LFO

---

### Layer 3: Classic House Clap

```javascript
s("~ cp ~ cp")
  .gain(0.7)
  .room(0.3)
  .delay(0.125)
  .delayfeedback(0.2)
```

**What it does:** Claps on beats 2 and 4 — the backbeat that makes you want to move.

**Breaking it down:**
- `~ cp ~ cp` — Rest, clap, rest, clap (beats 2 and 4)
- `.room(0.3)` — Adds reverb for space
- `.delay(0.125)` — Adds a short echo
- `.delayfeedback(0.2)` — Controls how many times the echo repeats

---

### Layer 4: Eerie Minor Chord Stabs

```javascript
note("<[c4,eb4,gb4] ~ ~ [c4,eb4,gb4] ~ ~ ~ ~> <[ab3,b3,eb4] ~ ~ [ab3,b3,eb4] ~ ~ ~ ~> ...")
  .sound("sawtooth")
  .lpf(sine.range(800, 3000).slow(8))
  .lpq(8)
  .gain(0.45)
  .attack(0.01)
  .decay(0.15)
  .sustain(0.3)
  .release(0.2)
  .room(0.25)
```

**What it does:** Sharp, dissonant chord stabs that give the track its haunted character.

**Breaking it down:**
- `[c4,eb4,gb4]` — Commas inside brackets play notes simultaneously as a chord (C diminished)
- `<...>` — Angle brackets alternate between different chords each cycle
- `~ ~ ~` — Rests create the stabbing rhythm
- `.sound("sawtooth")` — Uses a sawtooth synthesizer for that classic house sound
- `.lpf(sine.range(800, 3000).slow(8))` — Filter sweeps slowly between 800Hz and 3000Hz
- `.lpq(8)` — High resonance makes the filter sweep more pronounced
- `.attack(0.01)` — Very fast attack for punchy stabs
- `.decay(0.15)` / `.sustain(0.3)` / `.release(0.2)` — Short envelope for staccato feel

---

### Layer 5: Creeping Bass Line

```javascript
note("<c2 c2 c2 b1 bb1 bb1 ab1 ab1 g1 g1 gb1 gb1 f1 f1 e1 e1>/4")
  .sound("sawtooth")
  .lpf(400)
  .gain(0.7)
  .attack(0.01)
  .decay(0.1)
  .sustain(0.8)
  .release(0.1)
```

**What it does:** A chromatic bass line that slowly descends, creating tension and unease.

**Breaking it down:**
- The notes descend chromatically: C → B → Bb → Ab → G → Gb → F → E
- `/4` — Slows the pattern to play over 4 cycles (very slow descent)
- `.lpf(400)` — Heavy low-pass filter keeps only the deep bass frequencies
- `.sustain(0.8)` — Notes hold at 80% volume for a sustained bass sound

---

### Layer 6: Spooky Arp

```javascript
note("<[c5 eb5 gb5 a5] [ab4 b4 d5 f5] [g4 bb4 db5 e5] [gb4 a4 c5 eb5]>")
  .sound("triangle")
  .gain(0.35)
  .attack(0.02)
  .release(0.3)
  .lpf(2500)
  .room(0.4)
  .delay(0.166)
  .delayfeedback(0.35)
  .pan(sine.range(0.2, 0.8).slow(4))
  .every(4, x => x.rev())
```

**What it does:** Rising arpeggios built on diminished patterns that sound like shadows crawling.

**Breaking it down:**
- `[c5 eb5 gb5 a5]` — Four notes played in sequence within one beat
- Each arpeggio uses diminished intervals (minor thirds) for that spooky sound
- `.sound("triangle")` — Softer triangle wave synth
- `.pan(sine.range(0.2, 0.8).slow(4))` — Slow panning across the stereo field
- `.every(4, x => x.rev())` — Every 4 cycles, reverses the pattern

---

### Layer 7: Ghostly Pad

```javascript
note("<[c3,eb3,gb3,bb3] [ab2,b2,d3,f3] [g2,bb2,db3,e3] [gb2,a2,c3,eb3]>/2")
  .sound("sine")
  .gain(0.3)
  .attack(0.5)
  .release(1)
  .room(0.7)
  .lpf(1200)
```

**What it does:** A slow, evolving pad texture that fills out the harmonic space.

**Breaking it down:**
- Four-note chords played simultaneously
- `/2` — Each chord lasts 2 cycles (very slow)
- `.sound("sine")` — Pure sine wave for a smooth, ethereal sound
- `.attack(0.5)` — Slow fade-in (half second)
- `.release(1)` — Long fade-out (1 second)
- `.room(0.7)` — Lots of reverb for atmosphere

---

### Layer 8: Witch Cackle Percussion

```javascript
s("<oh ~ ~ oh:2 ~ ~ ~ ~> <~ ~ oh:3 ~ ~ ~ oh:1 ~>")
  .gain(0.4)
  .hpf(3000)
  .room(0.5)
  .speed("<1 1.2 0.8 1.5>")
  .sometimes(x => x.delay(0.25))
```

**What it does:** Open hi-hat hits with pitch shifting that sound like witch cackles.

**Breaking it down:**
- `oh:2`, `oh:3`, `oh:1` — Different variations of the open hi-hat sample
- `.hpf(3000)` — High-pass filter keeps only the bright, shrieky frequencies
- `.speed("<1 1.2 0.8 1.5>")` — Changes playback speed each cycle, shifting the pitch
- `.sometimes(x => x.delay(0.25))` — 50% of the time, adds delay

---

### Layer 9: Sub Bass Pulse

```javascript
note("<c1 ~ ab0 ~ g0 ~ gb0 ~>/2")
  .sound("sine")
  .gain(0.6)
  .attack(0.05)
  .decay(0.2)
  .sustain(0.7)
  .release(0.3)
  .lpf(100)
```

**What it does:** Deep sub-bass notes you feel more than hear.

**Breaking it down:**
- `c1`, `ab0`, `g0`, `gb0` — Very low octaves (0 and 1)
- `/2` — Plays over 2 cycles (slow)
- `.lpf(100)` — Extreme low-pass filter keeps only the deepest frequencies

---

### Layer 10: Ride Pattern

```javascript
s("~ ~ ~ ~, ~ [~ ride] ~ [~ ride]")
  .gain(0.35)
  .hpf(8000)
  .room(0.2)
```

**What it does:** Shimmering ride cymbals that add drive and energy.

**Breaking it down:**
- `~ [~ ride]` — Ride hits on the second half of beats 2 and 4
- `.hpf(8000)` — Very high-pass filter keeps only the shimmer

---

## Quick Reference: Functions Used

| Function | What It Does |
|----------|--------------|
| `setcpm(n)` | Sets tempo (cycles per minute, multiply by 4 for BPM) |
| `stack(...)` | Plays multiple patterns simultaneously |
| `s("...")` | Plays samples |
| `note("...")` | Plays musical notes |
| `.sound("...")` | Selects the synthesizer |
| `.gain(n)` | Volume (0-1) |
| `.lpf(n)` | Low-pass filter (Hz) |
| `.hpf(n)` | High-pass filter (Hz) |
| `.lpq(n)` | Filter resonance |
| `.room(n)` | Reverb amount (0-1) |
| `.delay(n)` | Echo timing |
| `.delayfeedback(n)` | Echo repetitions |
| `.attack(n)` | Note fade-in time |
| `.decay(n)` | Time to reach sustain level |
| `.sustain(n)` | Held volume level |
| `.release(n)` | Note fade-out time |
| `.pan(n)` | Stereo position (0=left, 1=right) |
| `.speed(n)` | Playback speed/pitch |
| `.every(n, fn)` | Apply function every n cycles |
| `.sometimes(fn)` | Apply function 50% of the time |

---

## Tips for Experimenting

1. **Change the tempo:** Try `setcpm(31)` for 124 BPM (classic house) or `setcpm(35)` for 140 BPM (more intense).

2. **Swap the chord voicings:** The stabs use diminished chords. Try changing `[c4,eb4,gb4]` to `[c4,eb4,g4]` for minor chords (less spooky, more classic house).

3. **Adjust the filter sweep:** Change `.lpf(sine.range(800, 3000).slow(8))` to `.lpf(sine.range(400, 5000).slow(4))` for a more dramatic sweep.

4. **More ghost notes:** Change `hh*8?` to `hh*16?` for busier, more chaotic hi-hats.

5. **Remove the spooky elements:** Comment out the witch cackle layer (add `//` at the start) for a more straightforward house track.

6. **Add more reverb:** Increase `.room(0.8)` on the pad for a more spacious, atmospheric feel.

7. **Change the bass pattern:** Try a different rhythm like `"c2 ~ c2 ~"` for a more driving bass.

8. **Experiment with the arp:** Change `.every(4, x => x.rev())` to `.every(2, x => x.rev())` for more frequent reversals.

---

## Musical Techniques Used

- **Four-on-the-floor:** Kick on every beat — the foundation of house music
- **Offbeat hi-hats:** Creates the classic house groove
- **Backbeat claps:** Claps on 2 and 4 drive the rhythm forward
- **Chromatic descent:** Bass line moving by half steps creates tension
- **Diminished chords:** Intervals of minor thirds sound inherently unstable and spooky
- **Filter sweeps:** LFO-modulated filters add movement and interest
- **Ghost notes:** Random elements add human feel and unpredictability
- **Layered sub-bass:** Separate sub-bass layer adds weight without muddying the main bass

---

## Have Fun!

House music is all about the groove — once you have that four-on-the-floor kick and offbeat hi-hats, you can layer almost anything on top. Experiment with different chord progressions, bass patterns, and effects. The spooky elements can be dialed up or down depending on how haunted you want your dancefloor to be! 🎃🏚️