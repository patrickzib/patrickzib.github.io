# Quarto Academic Website

This repository contains a Quarto-based academic site that publishes to GitHub Pages.

## Structure

- `_quarto.yml` — global configuration (navigation, theme, deployment metadata).
- `index.qmd`, `about.qmd`, `publications.qmd`, `teaching.qmd`, `talks.qmd` — page content in Quarto Markdown.
- `styles.scss` — custom styling layered on top of the Bootstrap `cosmo` theme.
- `old_html/` — legacy assets (PDFs, images, GIFs). The folder is referenced via `resources` so Quarto copies it into `_site/`.

## Prerequisites

1. Install [Quarto CLI](https://quarto.org/docs/download/) locally.
2. Install a recent version of Pandoc (bundled with Quarto) and LaTeX if you plan to render PDFs.

## Local workflow

```bash
# Install once
quarto install extension quarto-ext/fontawesome

# Live preview
quarto preview

# Render static site into _site/
quarto render
```

Site metadata (title, nav links, social icons) lives in `_quarto.yml`. Update the placeholder values such as `<github-user>` and `<email@example.com>` before publishing.

## Deployment to GitHub Pages

1. Commit everything to the default branch (e.g., `main`) and push to GitHub.
2. Run `quarto use github-actions` to scaffold `.github/workflows/quarto-publish.yml` (or copy it from the Quarto docs). Commit the workflow.
3. In the GitHub repository settings, enable Pages and select "GitHub Actions" as the source.
4. Each push to `main` will trigger the workflow to render the site and deploy it to the `gh-pages` branch.
5. Visit `https://<github-user>.github.io/webpage/` after the action completes. If using a custom domain, set `website.site-url` in `_quarto.yml` and add `CNAME`.

## Next steps

- Replace placeholder biography/news content with your own.
- Add a `pubs.bib` file and convert `publications.qmd` to use Quarto's bibliography listings.
- Move assets from `old_html/` into structured folders (e.g., `assets/img/`, `assets/pdfs/`) over time.
