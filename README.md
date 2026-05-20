# HumanIsletsDoc

Documentation for the HumanIslets Project (https://doc.humanislets.com/).

## Versions

This repository hosts two versions of the documentation side-by-side:

- **v1 (frozen)** — top-level Bookdown sources (`index.Rmd`, `01-using-website.Rmd`, …) render into `docs/`.
  Served at `https://doc.humanislets.com/`.
  This version is **no longer edited**; it remains in place to support the original HumanIslets website.

- **v2 (active)** — Bookdown sources under `v2/` render into `docs/v2/`.
  Served at `https://doc.humanislets.com/v2/`.
  This is the documentation for HumanIslets 2.0 and is where ongoing updates land.

## Layout

```
HumanIsletsDoc/
├── _bookdown.yml, _output.yml, index.Rmd, 0*.Rmd, …  # v1 source (frozen)
├── docs/                # GitHub Pages root
│   ├── *.html           # v1 rendered output (frozen)
│   └── v2/              # v2 rendered output (built from v2/)
└── v2/                  # v2 source (active)
    ├── _bookdown.yml    # output_dir: ../docs/v2
    ├── _output.yml      # injects version banner via includes/
    ├── index.Rmd        # v2 landing page
    ├── 0*.Rmd
    └── includes/
        ├── in_header.html      # banner CSS
        └── version_banner.html # banner HTML
```

## Building

**v1** — do not rebuild. The frozen rendered HTML in `docs/` is the source of truth.

**v2** — build from inside the `v2/` directory:

```r
setwd("v2")
bookdown::render_book("index.Rmd")
```

Output lands in `../docs/v2/`. Commit both the source changes and the rebuilt HTML.
