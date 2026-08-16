# Luda Korobenko — website

Static site for GitHub Pages (Jekyll, no build step).

## Edit content

- **Bio / contact / research blurb** → `index.md`
- **Publications** → `_data/publications.yml`
- **Teaching** → `teaching.md`
- **CV** → replace `assets/pdfs/cv.pdf` with a new PDF

## Add a publication

1. Drop the PDF into `assets/pdfs/` (e.g. `assets/pdfs/my-paper.pdf`).
2. Add an entry to `_data/publications.yml`:

```yaml
- title: "My new paper"
  authors: "Lyudmila Korobenko, Jane Doe"
  year: 2026
  journal: "Journal of Functional Analysis"   # optional
  arxiv: "2601.00000"                         # optional
  pdf: "/assets/pdfs/my-paper.pdf"            # optional
  abstract: "Optional abstract shown behind a toggle."
```

Sorted newest first. Commit + push → live.

## Run locally

```bash
jekyll serve        # http://localhost:4000/luda-website/
```

Requires Ruby + Jekyll. On macOS with Homebrew:

```bash
brew install ruby
gem install jekyll
export PATH="$(brew --prefix ruby)/bin:$(gem env gemdir)/bin:$PATH"
```

Add that `export` to your `~/.zshrc` to make it permanent.

## Deploy

GitHub repo → Settings → Pages → deploy from branch `main`, folder `/ (root)`.
Site lives at `https://<username>.github.io/luda-website/`.
Update `baseurl` in `_config.yml` if you rename the repo.
