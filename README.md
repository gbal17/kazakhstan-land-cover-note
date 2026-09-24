# Kazakhstan land cover note

A short, figure-led note on the disaggregated classes of the three land cover
products selected for Kazakhstan (ESA CCI, GLC_FCS30D, GLAD GLCLU), prepared for
the First Technical Workshop on Land Degradation Monitoring and PRAIS Reporting,
Astana, 28 September – 1 October 2026.

Published at <https://gbal17.github.io/kazakhstan-land-cover-note/> and linked
from the title of the comparison application it describes.

## The file

`index.html` is the whole site. Every figure is embedded in it, so GitHub Pages
needs no build step, no theme and no assets folder.

## Publishing

This repository has no `gh` dependency — `gh` is not installed on the machine
this was prepared from.

1. Create the repository on github.com: **New repository**, owner `gbal17`,
   name `kazakhstan-land-cover-note`, **Public**. Leave "Add a README file",
   `.gitignore` and licence **unticked** — this folder already has a commit, and
   initialising on the server would create a second history to reconcile.
2. Push:

   ```bash
   git push -u origin main
   ```

3. Enable Pages: **Settings → Pages → Source: Deploy from a branch →
   Branch `main`, folder `/ (root)` → Save.**

The site appears a minute or two later.

## Updating

The note is generated. Rebuild it with `build.py` in
`Workshop_KAZ_2026/06_Outputs/short_note_build/`, copy the result over
`index.html`, then commit and push. Pages redeploys itself.

`NOTE_URL` in `Workshop_KAZ_2026/03_Technical_inputs/gee/03_LC_Products_Compare_2023.js`
points at the published address. If this repository is ever renamed, that line
has to change with it and the application has to be republished.

## Note

A GitHub Pages site is public to anyone and can be indexed by search engines.
The page carries no author, date or status line.
