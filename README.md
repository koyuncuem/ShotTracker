# ShotTrack

A single-file Mounjaro (tirzepatide) dose & weight tracker. No build step, no backend — just open `index.html`.

**Live app:** enable GitHub Pages for this repo (see below) and open `https://<your-username>.github.io/<repo-name>/`

## Features

- Log doses (mg, injection site, pain, notes) and daily weight (kg/lb, body fat %, muscle %)
- "Medication in your system" chart — estimated active tirzepatide from a ~5-day half-life model, colored by dose, with Week / Month / 3 months / All ranges and a 1–2 week projection
- Weight chart colored by the dose you were on at the time
- Import Shotsy CSV/Excel exports; export back to Shotsy-compatible CSV
- Light/dark theme, works on phone screens

## How your data gets in

The app looks for a **`data.csv`** file **in the same folder as `index.html`** every time the page loads, and merges any new entries from it (duplicates are skipped). So:

1. Export your data from Shotsy (or from the app itself via **Export CSV**)
2. Replace `data.csv` in this repo with that file (keep the name `data.csv`)
3. Commit & push — the online app picks it up on the next page reload

Easiest way without the command line: on the repo page, click `data.csv` → pencil icon (or **Add file → Upload files**) and upload the new export.

Anything you log directly in the online app is also remembered by your browser (localStorage), so manual entries survive reloads on the same device. `data.csv` is what syncs across devices.

> ⚠️ This repo is public if you use free GitHub Pages — your `data.csv` (weights, doses) is visible to anyone with the link.

## Setting up GitHub Pages (one time)

1. Create a new repository on GitHub and push this folder to it
2. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / root → Save**
3. After a minute, your app is at `https://<your-username>.github.io/<repo-name>/`

## Notes

- The half-life model is a simple estimate for visualization, not medical guidance.
- Opening `index.html` directly from disk (`file://`) also works, but `data.csv` auto-load only works when served over HTTP (Pages, or `python3 -m http.server` locally).
