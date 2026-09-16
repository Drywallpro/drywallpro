# Drywall Pro Services Website

Drywall Pro Services website, built as a [Jekyll](https://jekyllrb.com/) site and hosted on GitHub Pages at [drywallpros.ca](https://drywallpros.ca) (see `CNAME`).

## Where things are

| Path | What it is |
|---|---|
| `*.html` (root) | One file per page (`about.html`, `contact.html`, etc.). Each is just YAML front matter (title, description, per-page stylesheet, optional form/script settings) plus that page's unique body content. |
| `_layouts/default.html` | The shared HTML boilerplate (`<head>`, nav/footer includes, closing scripts) every page renders into. Edit this to change something site-wide. |
| `_includes/header.html` | The nav bar, shared by every page. Active-link highlighting is done here via Liquid (`page.url`). |
| `_includes/footer.html` | The shared footer. |
| `styles/` | One CSS file per page (`about.css`, `contact.css`, ...) plus the shared `style.css`. |
| `scripts/` | `main.js` (mobile nav toggle, scroll effects, etc.) and `gallery.js` (gallery-page filtering). |
| `images/` | Site images. |
| `Gemfile` / `Gemfile.lock` | Pins the `github-pages` gem so your local build matches what GitHub Pages actually runs. |
| `CNAME` | Custom domain config for GitHub Pages. |

### Adding/editing a page

Front matter at the top of each `.html` file controls the page:

```yaml
---
layout: default
title: "Page Title - Drywall Pro Services"
description: "Meta description for search engines."
styles: pagename.css        # loads styles/pagename.css
formspree_form: "#formId"   # optional, wires up a Formspree form on the page
extra_scripts:              # optional, extra <script src="..."> tags before </body>
  - scripts/example.js
---
```

Everything below the closing `---` is just the page's unique body HTML — no `<html>`, `<head>`, `<nav>`, or `<footer>` needed, the layout supplies those.

## Running it locally

Requires Ruby (this project uses Ruby 3.3 with the MSYS2/DevKit toolchain on Windows, installed via `winget install --id RubyInstallerTeam.RubyWithDevKit.3.3`).

One-time setup:

```powershell
gem install bundler
bundle install
```

Build once (outputs static files to `_site/`, gitignored):

```powershell
bundle exec jekyll build
```

Serve locally with live-reload at `http://localhost:4000`:

```powershell
bundle exec jekyll serve
```

Ctrl+C stops the server. If a Windows PATH refresh is needed after installing Ruby, open a new terminal window first.
