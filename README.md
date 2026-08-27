# YFIO LLC — website

Static marketing site for **YFIO LLC (You Figure It Out)**, which provides vendoring and
merchandising services to venues in Colorado.

Plain HTML, CSS, and a few lines of JavaScript. No build step, no dependencies.

## Structure

```
index.html         Home
services.html      Services
venues.html        Venue list (carries a "last updated" date -- bump it when you edit)
experience.html    Experience & staff
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

The workflow turns Pages on by itself (`configure-pages` with `enablement: true`), so
there is nothing to click in **Settings → Pages**. The site publishes to
https://vincentdavis.github.io/yfioco/

`claude/yfio-static-site-s14eg6` is currently the repository's default branch, since it
was the first branch pushed. If you rename it to `main`, trim the workflow's `branches:`
list down to `main`.

### Custom domain

Add a file named `CNAME` at the repository root containing just the domain
(for example `yfiomerch.com`), point the DNS records at GitHub Pages, and set the domain
under **Settings → Pages**.

## Still to add

- **Phone / mailing address** — not on the site yet; add to `contact.html` when available.
- **Track record numbers** — `experience.html` has a commented-out block for years in business,
  events per season, venues served, and roster size. Left blank rather than guessed at.
- **Copy** — the service descriptions on `index.html` and `services.html` are a starting
  point written to be edited, not final marketing copy.
- **Social links, photos, client list, team bios** — none yet.

The contact address is `info@yfiomerch.com`, in `contact.html` and in the footer of every
page. Changing it means editing all five pages — `grep -rl info@yfiomerch.com *.html`
lists them.

## Adding a page

Copy an existing page, change the `<title>`, the `<meta name="description">`, and the body
content, then add a link to it in the header `<nav>` and the footer of every page.
