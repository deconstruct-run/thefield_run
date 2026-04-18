# theFIELD.run — PWA deploy bundle

This folder is a drop-in GitHub Pages site. Deploying it gives you an
installable, offline-capable Progressive Web App on iOS, Android, and desktop.

## Contents

- `index.html` — the full offline bundle with PWA head injections + service worker registration
- `manifest.webmanifest` — PWA manifest (name, icons, display mode)
- `sw.js` — service worker (cache-first, offline-capable)
- `icon-180.png`, `icon-192.png`, `icon-512.png` — brand icons

## Deploy to GitHub Pages

1. Create a new public repo on GitHub. Recommended name: `thefield-run`.
2. From this folder, push the contents to the repo root:

       cd thefield_run_pwa
       git init
       git add .
       git commit -m "Initial PWA deploy"
       git branch -M main
       git remote add origin https://github.com/<your-username>/thefield-run.git
       git push -u origin main

3. In the GitHub repo, open **Settings → Pages**.
4. Under *Build and deployment*, set **Source** to "Deploy from a branch".
5. Select branch `main`, folder `/ (root)`. Save.
6. Wait ~30-60 seconds. GitHub returns a URL like
   `https://<your-username>.github.io/thefield-run/`.

## Install on iPhone / iPad

1. Open Safari on iOS.
2. Visit `https://<your-username>.github.io/thefield-run/`.
3. Tap the **Share** icon (square with up-arrow) at the bottom of Safari.
4. Scroll and tap **Add to Home Screen**.
5. Name shows as "theFIELD". Tap **Add**.
6. First launch: wait ~5 seconds for the service worker to cache everything.
7. After first launch, turn on Airplane Mode and verify it still works. It should.

## Install on Android

1. Open Chrome on Android.
2. Visit the URL.
3. Chrome shows an install banner, or tap menu -> **Install app**.

## Updating the content

When you rebuild the offline HTML and re-run `build_pwa.py`:

1. Bump the `CACHE` version string in `sw.js` (e.g., `thefield-run-v2`).
2. Commit + push.
3. The service worker detects the new version and swaps the cache on next launch.
