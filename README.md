# FFFF — Fast Feedback Frequency Finder

A logarithmic tone generator and feedback finder for live sound. Single-page,
no build step, no dependencies, works offline as an installable PWA.

## What it does

- **Logarithmic frequency slider** — equal travel per octave, so the useful
  range isn't crammed into the left.
- **Band ladder** — tappable ISO 1/3-octave centres (80 Hz … 10 kHz) that map
  straight to graphic-EQ faders.
- **Range toggle** — 70 Hz–10 kHz (feedback) or full 20 Hz–22 kHz.
- **Sweep** — a logarithmic glide with a speed control; tap the readout mid-sweep
  to freeze on the ringing frequency.
- **Listen** — mic input, live log-spectrum, and dominant-peak detection (with
  nearest note and the matching band); tap the reading to load it into the tone.

## Run locally

Mic needs a secure context. `localhost` counts, so:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Opening `index.html` as a `file://` will run the generator but the mic will be
blocked.

## Deploy (GitHub Pages)

Either:

- **Branch:** Settings → Pages → Deploy from a branch → `main` / `root`. or
- **Actions:** Settings → Pages → Source = GitHub Actions (uses the included
  workflow in `.github/workflows/pages.yml`).

Paths are all relative, so it works under a project path
(`username.github.io/ffff/`). Over https the mic works and the app is
installable to the home screen.

## Known limits

- Phone speakers reproduce nothing below ~500 Hz — the low end is for the PA,
  not the handset.
- The mic is uncalibrated and iOS voice-processes; treat Listen as "which band
  is ringing", not a measurement. Constraints request EC/NS/AGC off.

## Roadmap

- Import-your-own-WAV pads for licensed samples.
- Peak-hold on the spectrum.
- Native iOS wrap: `playback` audio-session category (sound through the mute
  switch) and a mic-usage string — neither is reachable from the web layer.

## Licence

MIT. Change the holder/licence if you'd rather — this is a placeholder default.
