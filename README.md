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

**That URL is already wired into the application.** `NOTE_URL` points at it in every version of the
app script from `03_LC_Products_Compare_2023.js` to `17_LC_Products_Compare_2023_AllVariants_PanelToggle.js`, so the app title
links there with no change needed. If you use a different repository
name, the one line has to change with it.

To update the note later, rebuild it with `../short_note_build/build2.py`, copy
the result over `index.html`, then commit and push. Pages redeploys itself.

    cd ~/Desktop/K/Workshop_KAZ_2026/06_Outputs/short_note_build
    python3 build2.py ../KAZ_LC_products_short_note.html
    cp ../KAZ_LC_products_short_note.html ../github_pages/index.html
    cd ../github_pages && git add index.html && git commit -m "..." && git push

`build.py` built the older three-product note and is kept only for reference;
`build2.py` is the current one. It is bilingual: the page opens in English and
the two buttons at the top switch to Russian, so one URL serves both. Adding
`?lang=ru` opens it in Russian directly, which is the link to send to Kazakh
colleagues.

## Note

A GitHub Pages site is public to anyone and can be indexed by search engines.
The page currently carries no author, date or status line.
