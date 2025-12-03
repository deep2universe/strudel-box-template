---
inclusion: fileMatch
fileMatchPattern: '**/*.strudel'
---

# Tech Stack

## Runtime
- Audio: `@strudel/web` (CDN-loaded, no imports needed)
- Editor: CodeMirror 6 in VS Code Webview
- Syntax: JavaScript ES2020+ (synchronous only, no async/await)

## Available Samples
Use these sample names directly in `s()` or `sound()`:
- Drums: `bd`, `sd`, `hh`, `cp`, `oh`, `lt`, `mt`, `ht` (from tidal-drum-machines)
- Machines: TR-808, TR-909, TR-707 variants
- Instruments: `piano`, `EmuSP12`
- General: `Dirt-Samples`, `vcsl`

## Built-in Synths
Always available without loading: `sawtooth`, `sine`, `square`, `triangle`

## Not Supported
Do NOT use these (require full strudel.cc REPL):
- `@strudel/csound`, `@strudel/hydra`, `@strudel/tidal`
- Advanced MIDI, Device Motion APIs
- External imports or require statements

## Code Patterns
- All Strudel functions are globally available
- Use dot-chaining: `s("bd sd").fast(2).gain(0.8)`
- Layer with `stack()`: `stack(drums, bass, melody)`
- Set tempo with `setcpm(120)`
- Always end chains with `.gain(0.8)` to prevent clipping
