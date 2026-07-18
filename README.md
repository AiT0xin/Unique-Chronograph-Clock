# F.P. Journe Centigraphe Souverain — Live

A live SVG recreation of the F.P. Journe Centigraphe Souverain — the first hand-wound
wristwatch to measure elapsed times from 1/100th of a second to 10 minutes — synced to
atomic time.

Open `index.html` (or serve the folder) and the watch runs:

- **Hour / minute hands** — blued steel, driven by atomic-synced time.
- **100th-of-a-second register (SPR 1, left)** — the foudroyante hand sweeps once per
  second, continuously.
- **20-second register (SPR 20, right)** and **10-minute register (MPR 10, bottom)** —
  in the default mode all three registers track the atomic cycle (position within the
  current second / 20 s / 10 min span).
- **Rocker at 2 o'clock** (or the space bar) — works like the real one: press to start
  the chronograph from zero, press again to stop, press a third time to reset back to
  atomic-cycle mode. The crown at 4 o'clock is a matching grooved rectangular knob.
- **Triple-click** the watch to toggle a dark page background (persisted).

The rendering is watch-head only: no straps, no dial signatures, no caption — just the
dial. Sync happens silently in the background.

## Atomic sync

Multi-source consensus (same engine as the AP Royal Oak clock): worldtimeapi.org,
timeapi.io, and the origin server's HTTP `Date` header (with second-edge detection for
sub-second precision). Sources that disagree by >1.5 s are outvoted; re-syncs every
10 minutes with exponential backoff on failure.

URL parameter `?at=<ISO datetime>` freezes the watch at a simulated moment.

## Run locally

```sh
python3 -m http.server 8000 --directory .
```

Or via the Claude Code launch config: `journe-clock`.
