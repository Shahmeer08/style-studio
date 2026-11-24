# STYLE STUDIO v1.0 — Local-first wardrobe manager

## What this first version does
- Add clothing items with photos, categories, colours, seasons, fit, occasion and notes.
- Search and filter your wardrobe.
- Edit and delete items.
- Select wardrobe pieces and save outfit combinations.
- Export and import a full JSON backup, including photos.
- Works offline after the first successful load when installed/hosted as a PWA.

## Privacy model
- No login, analytics, advertising, tracking, cloud database or external AI calls.
- Wardrobe records and images are stored in IndexedDB in the browser on that device.
- The app shell (HTML/CSS/JS) must be served from a secure HTTPS origin for iPhone installation. Hosting the app shell does NOT send wardrobe photos or records to the host.
- Browser storage is not encrypted by this app. Protect the iPhone with its passcode/Face ID.
- Safari site data can be removed by the user or the operating system. Export backups regularly.
- This version does not automatically sync the database to iCloud. You can save exported backup files manually to iCloud Drive or the Files app.
- Do not assume iCloud device backup includes this PWA's browser database.

## Install on iPhone
1. Publish the contents of this folder to a static HTTPS host (for example, a GitHub Pages site). Do not upload any personal wardrobe data; only publish these app files.
2. Open the published HTTPS address in Safari on your iPhone.
3. Tap Share → Add to Home Screen → Add.
4. Launch Style Studio from the Home Screen.
5. Add a test item, export a backup, and confirm the JSON file appears in Files before adding your full wardrobe.

## Important
This is a functional MVP, not a native iOS application. It does not use Face ID locking, native iCloud sync, or AI analysis yet. Those require a later native iOS development/signing workflow or carefully chosen on-device capabilities.

## Run locally on Windows for preview
Use a local development server (not by double-clicking index.html) so IndexedDB and service worker behavior can be tested consistently. For example, with Python installed:
`python -m http.server 8000`
Then open `http://localhost:8000` on the Windows computer.
