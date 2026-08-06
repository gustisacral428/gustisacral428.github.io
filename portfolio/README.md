# erwin-portfolio

Personal portfolio site — Data & BI Analyst. Single static page, no build step, no dependencies.

Live at: `https://glcapitan.github.io/` (see setup below)

## Fill these in before publishing

1. **Email** — `index.html` has `mailto:your.email@example.com` in the Contact section. Replace it.
   (It's the only placeholder that will look wrong if you publish without editing.)
2. **Headshot** — drop your photo at `assets/headshot.jpg` (portrait crop, roughly 800×1000px). If the file is missing the page falls back to an "EC" monogram, so it never looks broken.
3. **Résumé** — drop your PDF at `assets/resume.pdf`. Two links point there.

Everything else — projects, repos, stack, work history — is already filled in with your real content.

## Publish it

**Option A — user site (recommended, gives you `glcapitan.github.io`)**

```bash
# create a repo on GitHub named exactly: glcapitan.github.io
git init
git add .
git commit -m "Portfolio site"
git branch -M main
git remote add origin https://github.com/glcapitan/glcapitan.github.io.git
git push -u origin main
```

Then: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save.**
Live in about a minute.

**Option B — project site** (any repo name, e.g. `portfolio`): same steps, and the URL becomes `https://glcapitan.github.io/portfolio/`.

## Custom domain (optional)

Add a file named `CNAME` containing just your domain (e.g. `erwincapitan.com`), point an ALIAS/A record at GitHub Pages, then set it under Settings → Pages.

## Structure

```
index.html                      the main page
projects/
  fabric-retail.html            case study pages, one per project
  azure-lakehouse.html
  supply-chain.html
  tableau-sales.html
  financial-dashboard.html
  nyc-taxi.html
  fintech-fraud.html
assets/
  headshot.jpg                  your photo (add this)
  resume.pdf                    your resume (add this)
  logos/                        optional logo overrides
```

Every page is self-contained — no shared stylesheet, no build step. Editing one page never
breaks another.

## Screenshots

Every project image is pulled straight from the matching GitHub repo over `raw.githubusercontent.com`,
so the site shows real screenshots the moment it goes live — nothing to upload.

If you'd rather host them alongside the site (faster, and immune to a repo rename), copy the images
into `assets/projects/<slug>/` and swap the `src` values. The slugs are `fabric-retail`,
`azure-lakehouse`, `supply-chain`, `tableau-sales`, `financial-dashboard`, `nyc-taxi`,
`fintech-fraud`.

Any image that fails to load is removed from the page automatically, so a renamed file degrades
quietly instead of showing a broken frame.

## Certifications

The Credentials block near the bottom of `index.html` lists Full-Stack Data Analytics as earned,
with DP-700 and dbt Analytics Engineering marked in progress. Move a card out of `class="cert prog"`
to `class="cert"` and change the label to "Earned" when you pass one.

## Design notes

- Palette is bronze → silver → gold, taken from the medallion layers in your own builds.
- Type: Bricolage Grotesque (display), Public Sans (body), JetBrains Mono (labels and code).
- The medallion pipeline in the "How I build" section is the signature element — it's the one animated thing on the page.
- Responsive down to mobile, keyboard focus is visible, and `prefers-reduced-motion` turns the animation off.

## Editing

Section order lives in `index.html` top to bottom: hero → method → work → stack → path → contact.
To add a project: copy one `<a class="card reveal">` block inside `<div class="work">` on the home
page, then copy any file in `projects/` as a starting point for the case study and swap the text.
Each case study follows the same spine — why I built it, questions it answers, how I built it,
how I know it works, honest notes.

## Tool logos

The logos are **inlined as SVG directly in `index.html`** — no CDN, no image files, nothing to
install. They render offline and can't break.

- Databricks, Snowflake, Airflow, dbt, PostgreSQL, Python, Spark, GitHub and Streamlit use the
  official marks from [Simple Icons](https://simpleicons.org) (CC0).
- Simple Icons no longer ships the Microsoft or Tableau marks for trademark reasons, so
  Microsoft Fabric, Azure Data Factory, Power BI, SQL Server, Excel and Tableau are drawn as
  brand-coloured glyphs in the same 24×24 grid.

**To swap in an official logo:** save it as `assets/logos/<slug>.svg` and it replaces the inline
one automatically on page load — no code change. The slug is the `data-logo` value on that chip
in `index.html`, e.g.:

```
assets/logos/powerbi.svg
assets/logos/microsoftfabric.svg
assets/logos/tableau.svg
```

Concept chips (Kimball star schemas, SCD Type 1 & 2, medallion architecture, watermark
incremental loads, data quality validation, DAX & Power Query, executive reporting) intentionally
show a coloured dot instead of a logo — those are techniques, not products.

These are third-party trademarks, used to identify tools. Don't restyle them into anything that
implies endorsement.
