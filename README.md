# louis-richard.github.io

Source of my academic website, [louis-richard.github.io](https://louis-richard.github.io). It is a Jekyll site built and deployed by GitHub Pages from the `master` branch, based on the [Academic Pages](https://github.com/academicpages/academicpages.github.io) template (MIT licence, see `LICENSE`).

## Running locally

GitHub Pages builds with Ruby 3.x; Ruby 4 is not supported by the `github-pages` gem, and the system Ruby on macOS is too old. On macOS:

```bash
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"   # also add this line to ~/.zshrc
bundle install
bundle exec jekyll serve -l -H localhost
```

The site is then served at http://localhost:4000 and rebuilds on changes, except for `_config.yml`, which needs a restart.

## Where things live

| Content | Location |
|---|---|
| Site settings, sidebar profile, social links | `_config.yml` |
| Top navigation | `_data/navigation.yml` |
| Home page, CV, other pages | `_pages/` |
| Publications (generated, see below) | `_publications/` |
| Talks | `_talks/` |
| Teaching | `_teaching/` |
| News and press releases | `_posts/` |
| Profile picture | `images/profile.jpg` (400×400 JPEG) |
| Downloadable files (served at `/files/...`) | `files/` |

Every entry in `_talks/` and `_teaching/` needs a unique `permalink`, or one page silently overwrites another.

## Updating publications

Publication pages are generated from `markdown_generator/publications.bib`, which is exported from my reference manager:

1. Export the library to `markdown_generator/publications.bib`.
2. Run all cells of `markdown_generator/PubsFromBib.ipynb` from inside `markdown_generator/` (requires `pybtex`).
3. Check the diff in `_publications/` before committing.

The generator skips entries without a `journal` field, files `@phdthesis` entries under "Theses", and shortens author lists longer than 10 names to "first three et al. (incl. L. Richard)".
