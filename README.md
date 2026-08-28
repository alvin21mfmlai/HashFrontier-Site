# HashFrontier — project page

A standalone, single-file project page for **HashFrontier**: a reproducible multi-core
evaluation of birthday, distinguished-point and Pollard-rho collision search on
deliberately truncated SHA3-256.

Built directly on the GUARDIAN-NIDS stylesheet so the portfolio reads as one series. The
CSS is that page's design system verbatim — same tokens, nav, hero, section shell, cards,
stage rail, tables, chart shell, code tabs, callouts, accordion and footer — with the teal
accent swapped for gold and a small set of additions for the components this subject needs
(shared-prefix digest panels, the outcome matrix, the line chart and the byte-layout strip).

## Contents

```
index.html     the entire site — HTML, CSS and JS in one file
vercel.json    static config: clean URLs + security headers
README.md      this file
.gitignore
```

## Deploy to Vercel

**Option A — drag and drop**

1. Go to <https://vercel.com/new>.
2. Drag this folder onto the deploy area.
3. Framework preset: **Other**. Leave build command and output directory empty.
4. Deploy.

**Option B — Git**

```bash
git init
git add .
git commit -m "HashFrontier project page"
git branch -M main
git remote add origin https://github.com/<you>/hashfrontier-site.git
git push -u origin main
```

Then import the repository at <https://vercel.com/new>. Framework preset **Other**,
no build step. Every push to `main` redeploys.

**Option C — CLI**

```bash
npm i -g vercel
vercel        # preview
vercel --prod # production
```

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Editing the content

Every figure on the page lives in a named constant at the top of the `<script>` block,
each annotated with the report table it came from:

| Constant   | Source                                                    |
|------------|-----------------------------------------------------------|
| `MATRIX`   | Table 9 — complete frozen 24-configuration result matrix   |
| `PARAMS`   | Table 3 — width-specific parameters                        |
| `STORAGE`  | Table 1 — generic birthday-scale work and record storage   |
| `PAIRS`    | Table 10 — all 17 independently verified collision pairs   |
| `NOTES`    | §6.2–6.4 and §7 — per-configuration commentary             |

Structure mirrors GUARDIAN-NIDS section for section: 01 Overview, 02 Architecture,
03 Widths, 04 Method, 05 Engines, 06 Results, 07 Evidence, 08 Discussion, 09 Engineering,
with the same alternating `section.alt` background rhythm.

Editing a constant updates every chart, table, tooltip and detail panel that reads it.
Theme colours are CSS custom properties in `:root` — `--gold` is the accent, with `--blue`,
`--violet`, `--amber` and `--rose` as supporting hues. The per-engine colours used by the
charts, matrix and legends live in the `ENG` map in the script (birthday gold, DP blue,
rho violet); change them there and every chart follows.

## Notes

- Zero build step and zero runtime dependencies. All charts are hand-built SVG and CSS.
- The only external request is the Google Fonts stylesheet (Inter + JetBrains Mono),
  with full system-font fallback stacks.
- The repository link (`github.com/alvin21mfmlai/HashFrontier`) is currently **private**.
  It appears twice in `index.html` — update or remove those if that changes.
- Verified: all 24 matrix rows and all 17 collision pairs render exactly as published in
  the report; every rate reconciles with evaluations ÷ elapsed; the three representative
  collision pairs were re-truncated from their published full digests and match; no page
  horizontal overflow at 390 / 768 / 1024 / 1440 / 1920 px; every text/background pair
  clears WCAG AA.
