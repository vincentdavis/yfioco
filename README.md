# YFIO LLC — website

Static marketing site for **YFIO LLC (You Figure It Out)**, which provides vendoring and
merchandising services to venues in Colorado.

Plain HTML, CSS, and a few lines of JavaScript. No build step, no dependencies.

## Structure

```
index.html         Home
services.html      Services
about.html         About
contact.html       Contact
404.html           Not-found page (served by GitHub Pages)
assets/css/site.css   All styles
assets/js/site.js     Mobile nav toggle + footer year
assets/img/           Logo and favicon
robots.txt, sitemap.xml, .nojekyll
.github/workflows/pages.yml   Deploys the site to GitHub Pages
```

The header and footer are duplicated in each page on purpose — editing one page never
breaks another, and there is nothing to install or compile.

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Or just open `index.html` in a browser.

## Publishing

Deployment runs from `.github/workflows/pages.yml` on every push to the deploy branch.

**One-time setup in GitHub:** go to **Settings → Pages → Build and deployment**
and set **Source** to **GitHub Actions**. The first workflow run publishes the site to
https://vincentdavis.github.io/yfioco/

Once the site lives on `main`, trim the workflow's `branches:` list down to `main`.

### Custom domain

Add a file named `CNAME` at the repository root containing just the domain
(for example `yfio.com`), point the DNS records at GitHub Pages, and set the domain
under **Settings → Pages**.

## Before going live — placeholders to replace

Search the repository for `TODO` to find these:

- **Contact email** — `info@yfioco.com` appears in `contact.html` and in the footer of every
  page. Replace it with the real address.
- **Phone / mailing address** — not on the site yet; add to `contact.html` when available.
- **Copy** — the service descriptions on `index.html` and `services.html` are a starting
  point written to be edited, not final marketing copy.
- **Social links, photos, client list, team bios** — none yet.

## Adding a page

Copy an existing page, change the `<title>`, the `<meta name="description">`, and the body
content, then add a link to it in the header `<nav>` and the footer of every page.
