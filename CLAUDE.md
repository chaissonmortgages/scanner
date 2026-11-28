# Scanner app: notes for Claude Code

Personal document scanner PWA for Mack's Android phone. Not a product. Keep it simple.

## Structure
- `index.html`: the whole app (HTML, CSS, vanilla JS). No frameworks, no build step, no dependencies. The PDF writer is hand rolled (`makePdf`, JPEG pages with DCTDecode).
- `vendor/pdf.min.mjs`, `vendor/pdf.worker.min.mjs`: PDF.js (pdfjs-dist 6.5.438), loaded with a dynamic import only when a PDF is picked (`loadPdfJs`). The one library Mack asked for, to open PDFs.
- `sw.js`: offline cache. Bump `VERSION` on every change to `index.html`.
- `manifest.webmanifest`, icons: home screen install.

## How the code is laid out
- Pages live in IndexedDB (`scanner` db, `pages` store): `{ id, order, src (JPEG Blob, max 3000px), corners [[x,y] x4 normalized TL,TR,BR,BL], rot, filter, adj {b,c,s}, cropped }`. Doc settings in `meta` store under `doc`: `{ title, size, quality, lastFilter }`.
- Pipeline: `warped()` (perspective warp from `corners`) then `applyLook()` (preset + adjustments) then `toCanvas()` (rotation). `render(p, maxSide)` runs all of it.
- `whiten()` estimates the paper colour per cell and divides it out (shadow removal) for Magic, Clean and B&W.
- PDFs: `pdfToImages()` renders each page to a JPEG (max 2400px) and adds it as a page with full corners and the Original filter, skipping the crop step.
- `detect()` auto finds the page: Otsu threshold, largest bright blob, extreme corners. Returns null when unsure.
- Screens: `#home`, `#crop`, `#edit`, plus `#saveSheet` and `#moreSheet`.

## Style rules
- Mobile first, big tap targets. Runs on Android and as an installed desktop app on Mack's Windows PC. `DESKTOP` (fine pointer, not Android) turns on `setupDesktop()`: `body.desktop` CSS, no camera button, drag and drop, paste, keyboard, Save as via `showSaveFilePicker`, and `launchQueue` for file handlers in the manifest.
- Never use em dashes in UI text or comments.
- Don't add libraries or a build step unless asked.
