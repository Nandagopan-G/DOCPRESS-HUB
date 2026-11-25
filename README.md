# DOCPRESS HUB

A 100% client-side, zero-backend web application for compressing images to strict KB limits and merging mixed PDFs and images into a single PDF directly in the browser.

## Features
- **100% Private & Offline-Ready:** All compression, resizing, rotation, scan cleanup, and PDF merging happen locally in the browser with zero server uploads (`sw.js` caches assets for offline use, plus a standalone single-file bundle `docpress-hub.html`).
- **Smart Target-KB Image Compressor:**
  - Supports `JPG`, `PNG`, and `WebP` via drag-and-drop or file picker.
  - Binary search over JPEG quality with automatic dimension step-down to meet strict KB limits (e.g., exam, scholarship, and ID upload portals).
  - Quick portal presets (`Passport Photo ~40 KB`, `Signature ~25 KB`, `Form Document ~150 KB`, `ID / Certificate ~200 KB`).
  - Optional max width/height constraints with aspect-ratio lock enabled by default.
  - Transparent PNG/WebP areas are flattened onto solid white (`#FFFFFF`) for JPEG exports.
  - Side-by-side Original vs. Compressed live comparison, size reduction stats, and one-click download.
- **Multi-File PDF & Image Merger:**
  - Mix `PDF`, `JPG`/`JPEG`, `PNG` (and `WebP`) files in any order.
  - Drag-and-drop and keyboard-accessible queue reordering (`↑` / `↓`), `90°` rotation for both images and PDFs, and per-item removal.
  - Optional scan cleanup & enhancement (`Grayscale`, `High-Contrast Scan`, brightness/contrast sliders, and batch apply).
  - Graceful handling of encrypted/password-protected or corrupted PDFs without crashing the queue.
  - Configurable image page sizing (`Fit to A4` or `Match Original`) and instant `merged-document.pdf` download.

## Screenshots / Live Demo
- **Local Demo:** Open `docpress-hub.html` directly in your browser, or run locally at `http://localhost:8080`.
- **Screenshots:**
  <!-- Replace with your own screenshots, e.g. ![Compressor View](./screenshots/compressor.png) -->

## How to Run / Installation
### Option 1: Single-File Offline Bundle (Fastest)
1. Download `docpress-hub.html`.
2. Double-click `docpress-hub.html` to open it directly in any modern browser—no installation or server required.

### Option 2: Local Static Server (PWA + Offline Cache)
1. Download or clone the repository.
2. Start a local static server from the project folder:
   ```bash
   python -m http.server 8080
   ```
3. Open `http://localhost:8080` in your browser (or open `index.html` directly).

## Tech Stack
- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Browser APIs:** HTML5 `<canvas>`, `Blob`, `createImageBitmap`, `FileReader` / `ArrayBuffer`, `URL.createObjectURL`, Service Worker (`sw.js`)
- **PDF Engine:** [`pdf-lib`](https://pdf-lib.js.org/) (`v1.17.1`, vendored locally in `vendor/pdf-lib.min.js`)
