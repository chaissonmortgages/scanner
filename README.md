# Scanner

My own phone document scanner, like Tap Scanner. One HTML file, no build step, no server, no accounts. Android only.

## What it does

- **Camera** or **Upload** photos (pick several at once from the gallery)
- **Crop:** finds the page edges on its own, or drag the four corners (a zoom bubble shows up while dragging). The page gets straightened out flat
- **Presets:** Original, Magic color, Clean gray, B&W, Grayscale, Lighten, Vivid. Magic color and Clean gray take out shadows and make the paper white
- **Adjust:** brightness (threshold in B&W), contrast, sharpen. "Use on all" copies the look to every page
- **Pages:** rotate, re-crop, replace the photo, move earlier or later, delete. Swipe left and right to flip pages
- **Save PDF:** rename it, pick Letter, A4 or fit to photo, pick quality, then **Save to phone** (goes to Downloads) or **Share** straight to Drive
- The scan in progress is kept on the phone, so closing the app doesn't lose pages

## Hosting

Netlify project `mack-scanner-4t8w2`, linked to this repo. Every push to `main` redeploys, and the installed app grabs the new version the next time it opens with signal. Not linked from anywhere and kept out of search engines.

Install: open the link in Chrome on the phone, menu > Install app.

## Notes

- When you change `index.html`, bump `VERSION` in `sw.js` so installed copies update.
- Run locally: `python3 -m http.server 8000`, then open http://localhost:8000
