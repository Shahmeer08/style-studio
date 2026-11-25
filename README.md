# STYLE STUDIO v2.1.0 — Local Magic Cutout

## What's new
- Adds a one-tap Magic Cutout action to the Add Piece screen.
- Uses `@bg0/browser` with BiRefNet in the browser (WebGPU/WASM).
- The selected photo is processed on-device; the photo itself is not uploaded for inference.
- The first use downloads the model/runtime assets. Keep Safari open and connected to the internet until the model is ready.
- The cutout is shown for review before saving. The original image is retained in the item record when a cutout is applied, and can be restored while editing.
- The existing IndexedDB database name, version, and object stores are unchanged.

## Important limitations
- This is background removal, not semantic clothing extraction. If the clothing is being worn by a person, the model may keep the whole person. Single-garment photos on a plain or uncluttered background are the best starting point.
- The library documents an iOS-specific single-threaded WASM path and reports testing on a physical iPhone 13; iPhone 11 Pro / the user's exact Safari build still needs real-device testing. If Safari runs out of memory, stop and report the error; do not repeatedly retry large images.
- Model loading requires an internet connection the first time. Once downloaded, browser caching may allow later offline use, but Safari can evict cached assets.
- The app shell is served by GitHub Pages. Wardrobe photos and database records remain in local Safari storage.

## Privacy and licensing
- `@bg0/browser` is Apache-2.0. Its model exports are MIT-licensed according to the project's third-party notices.
- The model files are fetched from the model host on first use; image bytes are processed in the browser and are not sent to the model host.
- No cloud inference, account, API key, or wardrobe sync is added.

## Deploy on GitHub Pages
This project now uses Vite so the browser library's iOS worker/model assets can be emitted into the build and served from the same origin.
1. Upload the complete contents of this project to the repository's `main` branch, replacing the old app files. Do not upload any personal wardrobe backup.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Open the **Actions** tab and wait for **Deploy STYLE STUDIO** to finish successfully.
5. Open `https://shahmeer08.github.io/style-studio/` in normal Safari mode (not Private Browsing).

The database remains `style-studio-db`, version 1, with the existing `items` and `outfits` stores. Do not clear Safari website data. Export a backup before making the update if possible.
