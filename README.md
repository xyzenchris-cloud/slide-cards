# Little Quest

Little Quest is a self-contained, cozy one-question-at-a-time page. It includes question sets, optional shuffled order, a writing box, optional voice typing, and answer history saved in the browser on the current device. It does not need a server or database.

## Upload to GitHub Pages

1. Upload `index.html`, `404.html`, `manifest.webmanifest`, `sw.js`, the `icons` folder, `.nojekyll`, and this `README.md` to the repository.
2. In GitHub, open **Settings → Pages**.
3. Choose **Deploy from a branch**, select `main` and the repository root, then save.
4. Open the Pages URL GitHub provides. Because the files use relative links, the page also works inside a repository folder such as `https://USERNAME.github.io/REPO-NAME/`.

The `.nojekyll` file is empty. GitHub Pages does not require it for these files, but keeping it prevents Jekyll processing from changing how future static files are served.

## Install and use it offline

Open the GitHub Pages address over HTTPS in Chrome, Edge, or another supported browser. In **Settings → Install app**, use the browser's install button when it appears. On iPhone or iPad, use **Share → Add to Home Screen**. The app caches its own page and icons so the main experience can open offline; voice typing still needs an internet connection.

The service worker is scoped to this repository folder only. It checks for a newer page when the app opens and offers a calm **A new version is ready** message before applying an update.

## Update the page

Open `index.html` in a text editor. Near the top of the script, update `APP_VERSION` when publishing a new copy, and edit the `QUEST_SETS` section to change questions and hints. The Hint action opens a lightweight, plain-text modal for the current question only; its contents are prepared lazily and are not saved in refresh-memory data. The comments there also identify the storage prefix, animation speed, and starting settings.

## Manuscript PDF

The Manuscript button opens the saved PDF in a new browser tab. Choose a PDF from the device, or drag it into the Manuscript section in Settings. The selected PDF is stored in this browser's IndexedDB and is never uploaded, sent to a server, or included in answer backups. A new browser profile or device will require choosing the PDF again; clearing site data, private browsing, storage quota limits, or browser cleanup can also remove it.

The app does not bundle PDF.js, render pages, search inside the PDF, or upload the selected file. If you configure a bundled PDF in `index.html`, that file becomes public with the site and is opened as a normal same-folder PDF. Version `1.6.0` removes the old viewer cache on service-worker activation; when replacing an older upload, also remove any obsolete `vendor/pdfjs/` files from the published folder.

## Performance check

Settings includes an opt-in **Performance check**. It can show approximate FPS, slow moments, DOM and animation counts, managed timers, available memory information, saved-data size, temporary feature switches, and a 10-second test with a copyable report. The diagnostics are not saved and are disabled by default. The page also pauses decorative effects while hidden and keeps the manuscript path lightweight: startup reads metadata only, while the PDF blob is loaded only after the Manuscript button is clicked.

## Reference hints

The Hint chip opens a centered reference-answer modal showing the prepared answers stored in the `HINT_ANSWERS` block near the top of `index.html`. Hints are local page content, not a server feature; anyone who can view the page source can read them. Answers are plain text in a minimal, scrollable modal and are prepared only when opened. A small configurable XP cost can be enabled once per question.

## Resume place

When enabled, the app remembers the active set, shuffled order, current question, written answers, passes, review state, points, streak, and hint state in this browser for up to seven days. It does not save open panels, microphone state, or settings, and starting another set or leaving the set clears the saved place.

## Notes

Answer history and settings stay in the browser's local storage. Use the Settings panel's backup and restore controls before changing devices or clearing browser data. Voice typing depends on browser support and microphone permission; Chrome and Edge generally provide the best support. The online GitHub Pages version uses HTTPS, which gives browsers the best chance to remember microphone permission after **Allow** is selected. Safari and some mobile browsers may not offer speech recognition or an install prompt.
