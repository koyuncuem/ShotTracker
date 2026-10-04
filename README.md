# ShotTrack

A single-file Mounjaro (tirzepatide) dose & weight tracker. No build step, no backend — just open `index.html`.

**Live app:** enable GitHub Pages for this repo (see below) and open `https://koyuncuem.github.io/ShotTracker/`

## Features

- Log doses (mg, injection site, pain, notes) and daily weight (kg/lb, body fat %, muscle %)
- "Medication in your system" chart — estimated active tirzepatide from a ~5-day half-life model, colored by dose, with Week / Month / 3 months / All ranges and a 1–2 week projection
- Weight chart colored by the dose you were on at the time
- Import Shotsy CSV/Excel exports; export back to Shotsy-compatible CSV
- Light/dark theme, works on phone screens

## How your data gets in — and stays in sync

The app looks for a **`data.csv`** file **in the same folder as `index.html`** every time the page loads, and merges any new entries from it (duplicates are skipped).

**Automatic sync (recommended):** click the **Sync** button in the app and follow the instructions there. You create a fine-grained GitHub personal access token once (Settings → Developer settings → Personal access tokens → Fine-grained tokens; Repository access: *only this repo*; Permissions → Contents: *Read and write*), paste it into the app, and from then on every dose/weight you add, edit, or delete is committed back to `data.csv` on GitHub within seconds. Other devices pick it up on their next page load. The token is stored only in that browser's localStorage. Set it up once per browser/device you log from.

**Manual route (works without a token):** export from Shotsy (or via **Export CSV** in the app) and upload the file as `data.csv` on the repo page (click `data.csv` → upload/replace). The online app picks it up on the next reload.

Anything you log directly in the app is also remembered by your browser (localStorage), so entries survive reloads even before a sync completes.

Note: because `data.csv` auto-load only ever *adds* entries, a deletion made on one device can reappear on another device that still has the entry in its browser memory — delete it there too (it will sync the deletion back).

> ⚠️ This repo is public if you use free GitHub Pages — your `data.csv` (weights, doses) is visible to anyone with the link.

## Setting up GitHub Pages (one time)

1. Create a new repository on GitHub and push this folder to it
2. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / root → Save**
3. After a minute, your app is at `https://<your-username>.github.io/<repo-name>/`

## Notes

- The half-life model is a simple estimate for visualization, not medical guidance.
- Opening `index.html` directly from disk (`file://`) also works, but `data.csv` auto-load only works when served over HTTP (Pages, or `python3 -m http.server` locally).
