# mtfoa.org

Source for the Middle Tennessee Football Officials Association website, migrated off
WebsiteBuilder to GitHub Pages (Jekyll).

## How it's built

- `_layouts/default.html` is the shared page shell (doctype/head/fonts), wrapping every
  page with the same header and footer.
- `_includes/nav.html` and `_includes/footer.html` are the site header and footer —
  each is a self-contained block (its own `<style>`/`<script>`), carried over from the
  WebsiteBuilder version with one change: they now fall back to `location.href` to
  detect the current page instead of WebsiteBuilder's `AppsApi.getCurrentUrl()`.
- Every other page (`index.html`, `news.html`, etc.) is plain HTML with a small Jekyll
  front-matter block (`title`, `description`) at the top; the content itself is the
  same custom HTML/CSS/JS block that used to be pasted into a WebsiteBuilder "Embed
  HTML" widget.
- The backend (Google Apps Script + the "MTFOA Roster" Google Sheet) is completely
  unchanged — every page still talks to the same `script.google.com/macros/.../exec`
  URLs it always did.

## Editing a page

Edit the `.html` file directly, commit, and push to `main` — GitHub Pages rebuilds
and republishes automatically within a minute or two. No separate "publish" step.

## Local preview

```
bundle exec jekyll serve
```

(needs Ruby + `gem install bundler jekyll`; optional — GitHub Pages will build it
either way).
