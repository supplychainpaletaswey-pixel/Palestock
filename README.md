# Paletas Wey — Unified Operations Dashboard

One dashboard that combines the three Paletas Wey (Bali) operations tools into a
single, consistently themed interface:

| Tab | File | Purpose |
|-----|------|---------|
| 📋 **Form Stok** | `form.html` | Merchandiser visit / stock-entry form (with optional AI photo scan). |
| 🚚 **Pengiriman** | `delivery.html` | Live ice-cream delivery board — status, drivers, vehicles, proof of delivery, reschedule, pickups. |
| 📦 **Stock Coverage** | `coverage.html` | Stock coverage analytics — per flavor / store / area, nearly-expired list, un-visited stores, date issues. |

`index.html` is the shell: a shared coral header, a live clock, and tab
navigation that loads each page in a frame. Tabs are deep-linkable
(`index.html#form`, `#delivery`, `#coverage`).

## Unified theme

All three pages were restyled to one system:

- **Brand colour:** Paletas Wey coral `#d94f3d`
- **Font:** Inter
- **Neutrals / cards / status badges:** shared slate palette

The delivery board was already coral (the reference); the stock-entry form
(previously ocean blue) and the coverage dashboard (previously blue) were
recoloured to match.

## Demo mode vs. live data

These pages were originally **Google Apps Script web apps** — the form submits
with `google.script.run`, and both dashboards pull their data from Google
Sheets through the same channel.

On GitHub Pages there is no Apps Script backend, so the pages run in **demo
mode**: a clearly-labelled sample dataset is shown so every view renders, and
the form's Scan / Submit fail gracefully with a friendly message instead of
erroring. A banner at the top says so.

To run with **live data**, deploy these files behind your Google Apps Script
web app (HtmlService) so that `google.script.run` is available and the server
injects the real `BOOTSTRAP` / `getDashboard` data. When the backend is
present, the demo stubs switch themselves off automatically.

## Run locally

Any static server works, e.g.:

```bash
python3 -m http.server 8000
# then open http://localhost:8000/
```

## Deploy on GitHub Pages

Push this folder to a repository, then in **Settings → Pages** set the source
to the `main` branch (root). The site will be served at
`https://<user>.github.io/<repo>/`. The included `.nojekyll` file ensures all
assets are served as-is.
