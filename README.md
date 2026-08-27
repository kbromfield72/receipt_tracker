# Receipt Vault

A private, installable web app for storing receipt photos separately from your
phone's main camera roll. Point your phone's camera at a receipt from inside the
app, and it auto-fills the store name and receipt date using on-device OCR
(you can always correct it). Every receipt is stored locally on your device
(IndexedDB) — nothing is uploaded anywhere.

## Why you need to host it (quick, free, no coding)

Phones only allow "Add to Home Screen" installable apps, camera access, and
offline caching over **HTTPS**. Opening `index.html` straight from a file
won't unlock those. The fastest free option:

### Option A — Netlify Drop (easiest, ~1 minute)
1. Go to **app.netlify.com/drop** on your computer.
2. Drag the whole `receipt-vault` folder onto the page.
3. You'll get a live `https://...netlify.app` link — open it on your phone.

### Option B — GitHub Pages
1. Create a new GitHub repo, upload these 5 files to it.
2. Repo Settings → Pages → set source to the main branch.
3. Visit the `https://yourname.github.io/reponame/` URL it gives you.

## Installing on your phone

**Android (Chrome):** open the hosted link → menu (⋮) → **"Add to Home
screen" / "Install app"**.

**iPhone (Safari):** open the hosted link → Share icon → **"Add to Home
Screen"**.

It'll now sit on your home screen with its own icon and open full-screen,
just like a native app — separate from your camera roll.

## Files
- `index.html` — the app itself
- `manifest.json` — tells the phone how to install it
- `sw.js` — service worker, caches the app shell so it opens offline
- `icon-192.png` / `icon-512.png` — home screen icons

## Notes
- OCR auto-fill (store name + date) needs an internet connection the first
  time it loads its recognition engine; after that it works offline too.
  If it can't confidently find a store or date, it leaves those fields for
  you to fill in — nothing is ever guessed silently.
- Recognized stores out of the box: Tesco, Asda, Sainsbury's, Morrisons,
  Aldi, Lidl, Waitrose, M&S, Co-op, Iceland — but you can type any name.
- Want the data on a new phone? IndexedDB storage is per-device/per-browser,
  so it won't sync automatically. Ask if you'd like an export/import button
  added.
