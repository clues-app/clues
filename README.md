# Clues - a single-file web app for zero-install, 100% local data visualization

**Clues** (by [Clues.ai](https://clues.ai)) is a **single-file web app** for **zero-install, 100% local data visualization**: one HTML file that turns a spreadsheet into an interactive workshop of charts you can profile, filter, style, animate, map, and share - without writing a line of code or sending your data anywhere.

The entire application is **one `Clues.html` file that runs in your browser**. No server, no build step, no install, no account. Every **CSV or Excel** file you open is parsed and charted **entirely client-side** - your data never leaves your machine.

> Built for people who have data and questions but don't want to code - scientists, analysts, lab managers, students. Drop a file in, and Clues profiles it, flags oddities, and suggests charts you can build with one click.

## Why Clues, when a chatbot can also draw a chart?

Because you can't cite a chat. A chatbot's chart is a one-off - ask again tomorrow and the bins, colors, and layout change, and the method lives in a transcript nobody can review. Clues works the other way around: **the AI proposes, you review, and Clues draws deterministically from your data, every time.**

- **Same chart, every time** - each chart is defined by a compact, inspectable spec (your methods section), not a conversation.
- **Every edit accounted for** - sign a dataset and Clues can later verify the data is the signed source plus only its documented edits.
- **Context travels with the figure** - snapshots permanently caption the exact filters that produced them, and a shared session stays live and explorable, not a dead PNG at the end of an email chain.

## Features

- **Zero-install, one file** - download `Clues.html`, open it, done.
- **100% local & private** - client-side only; nothing is uploaded, no telemetry, no account. Optional **AES-GCM password encryption** on saved sessions and shared files.
- **Loads CSV & Excel** - drag-and-drop a `.csv`, `.xlsx`, or `.xls`, or reopen a saved `.clue` session.
- **Guided first read** - an automatic `describe()`-style profile with inline mini-histograms, `value_counts` sparklines, IQR outlier flags, and one-click chart suggestions.
- **A full chart library**, all powered by [Plotly.js](https://plotly.com/javascript/):
  - **Relationships** - scatter (trendline, jitter, size / color / style-by, marginals, faceting), density, scatter matrix, correlation heatmap, **3D** scatter & line, parallel coordinates, **point maps**.
  - **Distributions** - box, violin, histogram, ECDF, ridgeline, 3D histograms.
  - **Comparisons** - bar, KPI, gauge, pie / donut, funnel, grid, Sankey, parallel categories, sunburst / treemap / icicle, **region maps (choropleth)**.
  - **Over Time** - time series, average + spread band, control charts (±3σ), and **multi-measure overlays** with an optional second axis.
- **Maps with no token** - tile or plain outline basemaps for both points and regions; boundaries and tiles are fetched at render time so the file stays small.
- **Filter, select, and brush** - global filters, brushed selections saved as named groups, one-click outlier trimming, and every chart recomputes live.
- **Style once, reuse everywhere** - per-chart or global styling, a saveable **house-style** theme applied to new datasets, and per-series overrides.
- **AI-assisted, two ways** - hand any assistant (ChatGPT, Claude, Gemini) a precise brief and import back a spec that **builds a coached analysis** or **restyles your charts**; a **Boost** mode turns the analysis into a presentation-ready story.
- **Evidence you can trust** - **snapshots** caption the exact filters that made them; a passphrase-signed **audit trail** and a **byte-exact source-file check** (SHA-256) back up provenance.
- **Portable & shareable** - save a full session as a `.clue`, or export **one self-contained interactive HTML** anyone can open in a browser (no Clues, no install), optionally password-protected.
- **3D & animation** - rotate 3D scenes and export **spinning GIFs**.
- **Dark mode**, plus a version footer that stamps every shared file with the build that produced it.

## Quick start

1. **Download** [`Clues.html`](Clues.html) from this repository.
2. **Open it** in a modern browser (Chrome, Edge, Firefox, or Safari) - double-click, or serve the folder (`python -m http.server`) for the interactive-share self-read path.
3. Click **Load original …** for the built-in Palmer Penguins demo, or drag in your own **CSV or Excel** file.

No dependencies to install. (For "choose where to save" prompts on a `file://` page, turn on your browser's *"Ask where to save each file before downloading."*)

## Documentation

See the full **[User Guide](USER_GUIDE.md)** for every feature - loading data, the chart families, maps, filtering & selections, theming, fields, snapshots, 3D & GIF export, saving & sharing, password protection, the AI workflow, and the data-audit trail.

## Security & privacy

- **Everything stays local.** Your file is parsed and charted entirely in the browser - nothing is uploaded, and there is no telemetry or account. The only network requests are the version-pinned libraries (cached on first load) and, *only while a tile map is on screen*, its map tiles and region boundaries - the **Outline** basemap needs nothing. Once loaded, you can go offline and everything except tile maps keeps working.
- **Encryption is local.** Optional **AES-GCM** (with a 600,000-iteration PBKDF2-SHA256 key) protects saved `.clue` files and shared HTML at rest. There is no password recovery.
- **Provenance.** A saved session records the source file's **SHA-256**, so you can later confirm a file is byte-for-byte the one an analysis was built on; a passphrase-signed **audit trail** additionally verifies the data is the signed source plus only its documented edits.
- **Run Clues from the official source.** The "AI context" Clues copies for your assistant is a set of *instructions* it will follow, so a tampered copy could inject unwanted ones. Get `Clues.html` from **[github.com/clues-app/clues](https://github.com/clues-app/clues)** (or your own saved copy), and be cautious with one that someone else sends you.

## Built with (thank you!)

Clues stands on the shoulders of superb open-source libraries, version-pinned and loaded from their CDNs:

- **[Plotly.js](https://plotly.com/javascript/)** - the interactive charting engine behind every chart, map, and 3D scene. Incredible work by the Plotly team. If you outgrow a single file and want to publish, host, and share richer interactive data apps, see **[Plotly Cloud](https://plotly.com/cloud/)** and **[Plotly Studio](https://plotly.com/studio/)**.
- **[Babel](https://babeljs.io/)** - transpiles the app's JSX/React live in the browser, which is why Clues can be one file with no build tool.
- **[React](https://react.dev/)**, **[PapaParse](https://www.papaparse.com/)** (CSV), **[SheetJS](https://sheetjs.com/)** (Excel), **[Tailwind CSS](https://tailwindcss.com/)**, and **[gif.js](https://github.com/jnordberg/gif.js)** (animated-GIF export).

Encryption uses the browser's built-in **Web Crypto** (AES-GCM + PBKDF2) - entirely local. Built with the help of **Anthropic's Claude** (AI pair programming).

## License

Clues is released under the **[MIT License](LICENSE)** - free to use, modify, and share.

---

*Clues runs entirely in your browser. © Clues.ai 2026.*
