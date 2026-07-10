# Hugo Site — Anatole Theme

A ready-to-edit [Hugo](https://gohugo.io/) website using the
[Anatole](https://github.com/lxndrblz/anatole) theme, with automatic build and
deploy to GitHub Pages via GitHub Actions.

This repo is **not** the theme's `exampleSite/` structure — the example
content, config, and data have already been moved into the standard,
production Hugo directories (`content/`, `config/`, `data/`, `static/`) at the
project root, so you can edit them directly. The theme itself lives in
`themes/anatole/` as a plain copy of its files (not a git submodule).

## Directory structure

```
.
├── .github/workflows/hugo.yaml   # CI: builds the site and deploys to GitHub Pages
├── archetypes/                   # Front matter templates for `hugo new`
├── config/_default/              # Site configuration (split across a few files)
│   ├── hugo.toml                 # Main config (baseURL, title, markup, etc.)
│   ├── languages.toml            # Language definitions (English + Arabic demo)
│   ├── menus.en.toml             # English menu
│   ├── menus.ar.toml             # Arabic menu
│   └── params.toml               # Theme parameters (author, social links, etc.)
├── content/                      # Your pages and posts
│   ├── english/
│   └── arabic/
├── data/
│   └── portfolio.yml             # Data file used by the optional portfolio page
├── static/                       # Static assets (images, favicons) copied as-is
├── themes/anatole/                # The Anatole theme, copied in directly
├── LICENSE
└── README.md
```

## Getting started locally

1. Install [Hugo (extended)](https://gohugo.io/installation/) and
   [Dart Sass](https://sass-lang.com/dart-sass/) (Anatole's stylesheets need
   the extended Hugo binary + Dart Sass to compile).
2. Clone this repo and run:
   ```sh
   hugo server
   ```
3. Open `http://localhost:1313/`.

## Making it your own

- **Site config**: edit `config/_default/hugo.toml` (title, `baseURL`) and
  `config/_default/params.toml` (author info, social links, analytics, etc.).
- **Content**: edit or replace the demo pages/posts under `content/english/`
  (and `content/arabic/`, or delete that language entirely if you only want
  one language — remember to also update `config/_default/languages.toml`).
- **Portfolio**: edit `data/portfolio.yml` and
  `content/english/portfolio/_index.md`, or remove the portfolio page if you
  don't need it.
- **Images/favicon**: replace files under `static/images/` and
  `static/favicons/`.
- **Theme tweaks**: since `themes/anatole/` is a plain copy (not a submodule),
  you can edit its layouts/CSS/SCSS directly. Note this means you won't get
  theme updates automatically — see "Updating the theme" below.

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. In the repo, go to **Settings → Pages** and set **Source** to
   **GitHub Actions**.
3. Push to `main` (or run the workflow manually from the **Actions** tab).
   `.github/workflows/hugo.yaml` will build the site with Hugo (extended) and
   Dart Sass and deploy the result automatically. The workflow sets the
   correct `baseURL` for you at build time, so you don't need to hardcode your
   GitHub Pages URL in `hugo.toml` for the deployed site to work correctly.
4. Your site will be live at `https://<your-username>.github.io/<repo-name>/`
   (or `https://<your-username>.github.io/` if this is a user/organization
   site repo named `<your-username>.github.io`).

To use a custom domain, add a `static/CNAME` file containing your domain name
and configure DNS per
[GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Updating the theme

Because the theme is copied directly into `themes/anatole/` rather than
tracked as a git submodule, pulling upstream Anatole updates is a manual step:
download a newer release of https://github.com/lxndrblz/anatole and replace
the contents of `themes/anatole/` (re-applying any local edits you've made).

## License

The site scaffold itself (this README, GitHub Actions workflow, and config)
is provided under the MIT License — see [`LICENSE`](./LICENSE).

The bundled Anatole theme in `themes/anatole/` is © 2020 lxndrblz and
separately licensed under the MIT License — see
[`themes/anatole/LICENSE`](./themes/anatole/LICENSE).
