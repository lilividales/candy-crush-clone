# Kueh Crush — by Livac Designs

A 60-second, touch-friendly match-3 game with Peranakan kueh. Score **2,500** to unlock the **Kueh10** code for 10% off.
It's a Progressive Web App (PWA), so people can install it on their phone's home screen and play offline.

## What's in the repo

| File | What it does |
| --- | --- |
| `index.html` | The whole game: graphics, sounds, rules and the install button |
| `manifest.webmanifest` | App name, colours and icons, used when the game is installed |
| `sw.js` | Service worker: caches the game so it loads instantly and works offline |
| `icons/` | App icons (`icon.svg` and `icon-maskable.svg` are the editable sources) |
| `vercel.json` | Hosting settings for Vercel (cache headers for the service worker and manifest) |

No build step and no dependencies: it's plain static files.

## Deploy on Vercel

1. In Vercel, choose **Add New → Project** and import `lilividales/candy-crush-clone`.
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Click **Deploy**. Every push to `main` redeploys automatically.

## Install on a phone

- **Android (Chrome):** open the site and tap **Install Kueh Crush on this phone** on the start screen (or menu → *Install app*).
- **iPhone (Safari):** tap **Share → Add to Home Screen**.

## Changing the game

The settings sit on one line near the top of the script in `index.html`:

```js
const N=8, TYPES=6, ROUND=60, TARGET=2500, CODE='Kueh10', DISCOUNT='10% off';
```

`TARGET` also appears in the text of the start screen and the progress label, so update those too.

**After any change, bump `VERSION` in `sw.js`** (e.g. `kueh-crush-v2`), so installed copies pick up the update.

## Run locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

The service worker only runs over `http://localhost` or `https://`, not when you open the file directly.
