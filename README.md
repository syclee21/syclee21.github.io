# syclee21.github.io

Source for my personal academic website, live at **[syclee21.github.io](https://syclee21.github.io)**.

Built with [Quarto](https://quarto.org) and hosted on GitHub Pages.

## Structure

| File | Contents |
|---|---|
| `index.qmd` | About page |
| `research.qmd` | Research themes and projects |
| `publications.qmd` | Publications page; entries are in `publications.yml`, layout in `publications.ejs` |
| `failures.qmd` | CV of Failures |
| `_quarto.yml` | Site settings and navigation |
| `styles.css`, `theme-light.scss`, `theme-dark.scss` | Styling |

## Building locally

Requires [Quarto](https://quarto.org/docs/download/).

```bash
quarto preview            # live preview while editing
quarto publish gh-pages   # build and deploy to GitHub Pages
```

This `main` branch holds the source files; the built site is on the `gh-pages` branch.
