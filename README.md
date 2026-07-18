# F.P. Journe Centigraphe Souverain — Live

A live SVG recreation of the F.P. Journe Centigraphe Souverain — the first hand-wound
wristwatch to measure elapsed times from 1/100th of a second to 10 minutes — synced to
atomic time.

Open `index.html` (or serve the folder) and the watch runs:

- **Hour / minute hands** — blued steel, driven by atomic-synced time.
- **Three chronograph registers** — SPR 1 (100th-of-a-second foudroyante), SPR 20
  (20-second), and MPR 10 (10-minute) — sit at zero until started.
- **Rocker at 2 o'clock** (or the space bar) — a real stopwatch: press to start from
  zero, press again to stop, press a third time to fly back to zero. The crown at
  4 o'clock is a matching grooved rectangular knob.
- **Triple-click** the watch to toggle a dark page background.

The rendering is watch-head only: no straps, no dial signatures, no caption — just the
dial. Sync happens silently in the background.

## Embedding in Notion or a website

Once GitHub Pages is enabled for this repo (Settings → Pages → deploy from `main`,
root), the live page is at:

```
https://ait0xin.github.io/Unique-Chronograph-Clock/
```

Paste that URL into a Notion embed block, or use it as an `<iframe src="...">` on any
site. The page background is transparent by default so it blends into the page behind
it; triple-click the watch for a dark `#191919` background instead (useful against a
white Notion page). The toggle persists via **both** `localStorage` and a cookie,
independently — Notion's iframe sandbox can silently block one or the other, so having
both means the setting survives either way.

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
