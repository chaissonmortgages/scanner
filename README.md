# Scanner

My own phone document scanner, like Tap Scanner. One HTML file, no build step, no server, no accounts. Android only.

## What it does

- **Camera** or **Upload**: Photos (gallery) or Files / Drive (photos and PDFs). Each PDF page becomes a page you can crop, rotate or clean up
- **Crop:** finds the page edges on its own, or drag the four corners (a zoom bubble shows up while dragging). The page gets straightened out flat
- **Presets:** Original, Magic color, Clean gray, B&W, Grayscale, Lighten, Vivid. Magic color and Clean gray take out shadows and make the paper white
- **Adjust:** brightness (threshold in B&W), contrast, sharpen. "Use on all" copies the look to every page
- **Pages:** rotate one or all pages, re-crop, retake the photo, move earlier or later, delete. Swipe left and right to flip pages
- **Save PDF:** rename it, pick Letter, A4 or fit to photo, pick quality, then **Save to phone** (goes to Downloads) or **Share** straight to Drive
- The scan in progress is kept on the phone, so closing the app doesn't lose pages

## Hosting

Netlify project `mack-scanner-4t8w2`, linked to this repo. Every push to `main` redeploys, and the installed app grabs the new version the next time it opens with signal. Not linked from anywhere and kept out of search engines.

Install on the phone: open the link in Chrome, menu > Install app.

Install on the Windows PC: open the link in Chrome or Edge, click the install icon in the address bar (or menu > Cast, save and share > Install page as app). On the computer it gets a wide layout, drag and drop, Ctrl+V paste, a Save as window (pick your Google Drive folder), and Open with Scanner for PDFs and photos in File Explorer.

## Notes

- When you change `index.html`, bump `VERSION` in `sw.js` so installed copies update.
- Run locally: `python3 -m http.server 8000`, then open http://localhost:8000
