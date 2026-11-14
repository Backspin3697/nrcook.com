# nrcook.com

Source for [nrcook.com](https://nrcook.com): a static [Hugo](https://gohugo.io) site with no theme, no JavaScript and no third-party requests.

## Layout

- `content/_index.md` — the home page
- `layouts/` — templates (Hugo ≥ 0.146 template layout: `baseof.html`, `home.html`, `page.html`, `404.html`)
- `assets/css/site.css` — styles (minified and fingerprinted at build time; system font stack)
- `hugo.toml` — site config; `params.email` turns on the contact link

## Editing

```bash
hugo server        # local preview at http://localhost:1313
```

Push to `main`. The `publish` workflow builds with the Hugo version pinned in `.github/workflows/publish.yml` and force-pushes the generated site to the `publish` branch. The web server pulls `publish` every 15 minutes, so changes go live within about 15 minutes of a successful build.

## Constraints

The server sends a strict Content-Security-Policy (`default-src 'self'`). Inline `<style>`/`<script>` and resources from other origins are blocked; keep CSS in `assets/css/` and serve any fonts or images from this site.
