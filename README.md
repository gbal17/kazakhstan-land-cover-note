# Publishing this note on GitHub Pages

`index.html` is the complete note. It is self-contained — every figure is
embedded in the file — so GitHub Pages needs nothing else: no build, no theme,
no assets folder.

Run these on your Mac, where `gh` and your SSH key live. They are not runnable
from the Claude session, which has neither.

```bash
cd ~/Desktop/K/Workshop_KAZ_2026/06_Outputs/github_pages

git init -b main
git add index.html README.md
git commit -m "Land cover products note for the Astana workshop"

gh repo create gbal17/kazakhstan-land-cover-note --public
git remote add origin git@github.com:gbal17/kazakhstan-land-cover-note.git
git push -u origin main

gh api -X POST repos/gbal17/kazakhstan-land-cover-note/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

Without `gh`: create the repository on github.com, add the SSH remote and push
as above, then Settings → Pages → Source: `main`, folder `/ (root)`.

The site appears a minute or two later at

    https://gbal17.github.io/kazakhstan-land-cover-note/

**That URL is already wired into the application.** `NOTE_URL` in
`03_Technical_inputs/gee/03_LC_Products_Compare_2023.js` points at it, so the
app title links there once you republish. If you use a different repository
name, the one line has to change with it.

To update the note later, rebuild it with `../short_note_build/build.py`, copy
the result over `index.html`, then commit and push. Pages redeploys itself.

## Note

A GitHub Pages site is public to anyone and can be indexed by search engines.
The page currently carries no author, date or status line.
