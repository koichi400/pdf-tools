# PDF Tools — Merge, Split & Rotate in Your Browser

Merge, split, and rotate PDF files entirely in your browser. Your files never leave your device.

A static web app with no backend and no database. Every operation runs 100% locally in the visitor's browser, so there are no uploads, no server costs, and no file-size limits imposed by a server.

## Features

- **Merge** — Combine multiple PDFs into one, with drag-and-drop reordering
- **Split / Extract** — Click page thumbnails to select pages and extract them (kept in sync with a page-range field, e.g. `1-3,5`), or split every page into separate files as a ZIP
- **Rotate** — Rotate individual pages with the Left 90° / Right 90° buttons on each thumbnail (with a live preview), or rotate all pages at once

Page thumbnails are rendered at low resolution with PDF.js, so even long documents stay fast.

## Libraries (loaded from CDN)

- [pdf-lib](https://pdf-lib.js.org/) (MIT) — PDF manipulation
- [PDF.js](https://mozilla.github.io/pdf.js/) — thumbnail rendering
- [JSZip](https://stuk.github.io/jszip/) — ZIP download for split pages

Not supported: password-protected or encrypted PDFs.

## Internationalization (i18n)

The UI is available in English and Japanese, switchable with the **EN / 日本語** toggle in the top-right corner. On first visit the language is detected from the browser's language setting (Japanese environments get Japanese, everything else gets English), and the chosen language is saved in `localStorage` so it persists on the next visit.

All user-facing strings are managed centrally in a single dictionary object (`I18N`, with `en` and `ja` locales) at the top of the script in `index.html` — nothing is hard-coded in the markup or the logic. To add another language, add a locale object with the same keys.

## Deploy to Cloudflare Pages (free)

### Option A: GitHub integration (auto-deploy on push)

1. Push this folder to a GitHub repository
2. In the Cloudflare Dashboard, go to **Workers & Pages → Create → Pages → Connect to Git** and select the repository
3. Build settings:
   - Framework preset: `None`
   - Build command: *(leave empty)*
   - Build output directory: `/` (root)
4. Click **Save and Deploy** — the site goes live at `https://<project-name>.pages.dev`
5. Optional: attach a custom domain under **Custom domains** in the Pages project (e.g. `pdf.example.com`)

### Option B: Direct upload

In the Cloudflare Dashboard, go to **Workers & Pages → Create → Pages → Upload assets** and upload this folder (`index.html`).

### Option C: Wrangler CLI

```bash
npx wrangler pages deploy . --project-name pdf-tools
```

## Run locally

```bash
npx serve .
# or
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser.

## Files

- `index.html` — the entire app (this one file is all you need)
- `wrangler.toml` — Cloudflare configuration (optional)
- `README.md` — this file
- `LICENSE` — MIT License

## License

MIT License — see [LICENSE](LICENSE) for details.

Copyright (c) 2026 Koichi Uemura
