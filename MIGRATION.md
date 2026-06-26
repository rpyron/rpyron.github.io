# Squarespace to Academic Pages Migration

This repository now contains the Academic Pages Jekyll template for GitHub Pages.
Use this checklist to move scraped Squarespace content into the site.

## 1. Site identity

Edit `_config.yml`:

- `title`, `name`, `description`
- `url`: `https://YOUR-GITHUB-USERNAME.github.io`
- `repository`: `YOUR-GITHUB-USERNAME/YOUR-GITHUB-USERNAME.github.io`
- `author` fields for sidebar name, bio, affiliation, location, email, GitHub, Google Scholar, ORCID, LinkedIn, and other profiles

Place a profile image at `images/profile.png`, or update `author.avatar` to the
filename you prefer.

## 2. Main pages

Convert Squarespace pages into Markdown files under `_pages/`.

Common mappings:

- Home/About page: `_pages/about.md`
- CV page: `_pages/cv.md` or `_data/cv.json`
- Publications index: `_pages/publications.md`
- Talks index: `_pages/talks.md`
- Teaching page: `_pages/teaching.md`
- Extra pages: create new files in `_pages/` with a `permalink`

Each page needs YAML front matter at the top:

```yaml
---
title: "Page Title"
permalink: /page-url/
author_profile: true
---
```

## 3. Structured academic content

Academic Pages works best when repeated academic items become separate Markdown
files:

- Publications: `_publications/`
- Talks: `_talks/`
- Teaching entries: `_teaching/`
- Portfolio/projects: `_portfolio/`
- Blog/news posts: `_posts/`

Keep one item per file. Use the existing sample files as front matter examples,
then replace the sample text with real content from the Squarespace scrape.

## 4. Images, PDFs, and downloads

Move assets from the Squarespace scrape into:

- Images: `images/`
- PDFs, CV downloads, slides, datasets, and other files: `files/`

Reference them from Markdown like:

```markdown
[Download CV](/files/cv.pdf)
![Profile photo](/images/profile.png)
```

## 5. Navigation

Edit `_data/navigation.yml` to match the pages you want in the header. Remove
unused template links such as `Portfolio`, `Blog Posts`, or `Guide` if they do
not belong on the rebuilt site.

## 6. Squarespace URLs and redirects

If the old Squarespace site had URLs that should keep working, add
`redirect_from` entries to the new page front matter:

```yaml
redirect_from:
  - /old-squarespace-url/
  - /old-squarespace-url.html
```

## 7. Local preview

This machine currently has Ruby 2.6, which is too old for the latest resolved
Jekyll dependencies. Use one of these options before local previewing:

- Install Ruby 3.2 or newer, then run `bundle install` and `bundle exec jekyll serve`
- Install Docker, then run `docker compose up`
- Push to GitHub and let GitHub Pages build the site

After the server starts, open `http://localhost:4000`.
