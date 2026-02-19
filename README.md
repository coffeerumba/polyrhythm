# Polyrhythm Player

A browser-based polyrhythm player with polygon visualizer.

**Demo:** https://coffeerumba.github.io/polyrhythm/

## How It Works

Each line in the score defines a voice. Notes are separated by commas. The number of notes per line determines how many times that voice sounds per cycle — creating polyrhythms when lines have different note counts.

The cycle period `t` is derived from BPM: `t = 240 / bpm`. Each voice divides this period evenly among its notes (`t / p` seconds between each note).

## Score Format

```
C4,E4,G4
F3,A3
kick,hihat,snare,hihat
```

- **Tonal notes** — `C4`, `F#3`, `Bb5`, etc. (parsed by [tonal](https://github.com/tonaljs/tonal))
- **Drum names** — `kick`, `snare`, `hihat`, `clap`, `tom`
- **Mixed** — tonal notes and drums can coexist in the same line
- **Silent notes** — unrecognized strings are treated as rests
- **Empty lines** are ignored

## Visualizer

Each voice is displayed as a polygon with vertices equal to the note count:

| Notes | Shape |
|-------|-------|
| 1 | Point |
| 2 | Line |
| 3 | Triangle |
| 4 | Square |
| n | n-gon |

A dot traverses the polygon in sync with playback, highlighting briefly at each vertex when the corresponding note sounds.

## Controls

- **BPM slider** (15–300) — adjusts playback speed in real time
- **Play / Stop** — starts or stops playback

Score and BPM are saved to localStorage and restored on reload.

## Tech Stack

- [Tone.js](https://tonejs.github.io/) — audio scheduling and synthesis
- [Tonal](https://github.com/tonaljs/tonal) — music theory / note parsing
- [jQuery](https://jquery.com/) — DOM manipulation
- Canvas 2D — visualizer rendering

## Running Locally

Open `index.html` in a browser. No build step required.
