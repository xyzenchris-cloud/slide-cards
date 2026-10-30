# Little Quest

Little Quest is a self-contained, cozy one-question-at-a-time page. It includes question sets, optional shuffled order, a writing box, optional voice typing, and answer history saved in the browser on the current device. It does not need a server or database.

## Upload to GitHub Pages

1. Upload `index.html`, `404.html`, `.nojekyll`, and this `README.md` to the repository.
2. In GitHub, open **Settings → Pages**.
3. Choose **Deploy from a branch**, select `main` and the repository root, then save.
4. Open the Pages URL GitHub provides. Because the files use relative links, the page also works inside a repository folder such as `https://USERNAME.github.io/REPO-NAME/`.

The `.nojekyll` file is empty. GitHub Pages does not require it for these files, but keeping it prevents Jekyll processing from changing how future static files are served.

## Update the page

Open `index.html` in a text editor. Near the top of the script, update `APP_VERSION` when publishing a new copy, and edit the `QUEST_SETS` section to change questions and hints. The comments there also identify the storage prefix, animation speed, and starting settings.

## Notes

Answer history and settings stay in the browser's local storage. Use the Settings panel's backup and restore controls before changing devices or clearing browser data. Voice typing depends on browser support and microphone permission; Chrome and Edge generally provide the best support. The online GitHub Pages version uses HTTPS, which gives browsers the best chance to remember microphone permission after **Allow** is selected.
