# Agent Notes

This repository is a small Jekyll site for `zijian.page`.

## Working Rules

- Make changes in source files, not generated output.
- Do not edit `_site/`; it is a build artifact.
- Do not commit `vendor/`, `.bundle/`, `.jekyll-cache/`, or `_site/`.
- Prefer small, direct edits. The site is intentionally simple.
- The default branch is `main`.

## Repo Layout

- `_config.yml`: site-wide Jekyll config, including `site.title` and analytics.
- `_layouts/`: HTML layouts.
- `_sass/` and `assets/css/style.scss`: styles.
- `index.md`, `photos.md`, `links.md`, `media.md`: top-level pages.
- `_posts/`: photo post content used by the older photo-post flow.
- `assets/photos/`: image assets and placeholder gallery images.
- `docker-compose.yml`: recommended local dev entrypoint.

## Local Development

Recommended workflow:

```sh
docker compose up
```

This starts Jekyll with live reload.

Local URLs:

- Site: `http://localhost:4000`
- Live reload: `http://localhost:35729`

To stop the server:

```sh
docker compose down
```

If containers or networks get stale:

```sh
docker compose down --remove-orphans
```

## Rebuild After Dependency or Config Changes

If you change `Gemfile`, `Gemfile.lock`, or hit odd dependency issues, rebuild from scratch:

```sh
docker compose down --remove-orphans
rm -rf vendor/bundle .bundle .jekyll-cache _site
docker compose up
```

Use this carefully. It deletes local build artifacts only.

## Cleanup

Safe local cleanup targets in this repo:

```sh
rm -rf _site .jekyll-cache .bundle vendor/bundle
find . -name .DS_Store -delete
```

Do not delete:

- `assets/`
- `_posts/`
- `_layouts/`
- `_sass/`
- page markdown files

## Photos Page

- `photos.md` currently uses a JavaScript-driven single-image gallery.
- The gallery content lives inline in the `photos` array inside `photos.md`.
- Each item currently has:
  - `src`
  - `alt`
  - `caption`
- `Prev` and `Next` are simple links under the image.
- Clicking the image also advances the gallery.
- Left and right arrow keys cycle through the gallery.

When replacing placeholders with real images:

1. Add images under `assets/photos/`.
2. Update the `photos` array in `photos.md`.
3. Keep captions short unless the layout is adjusted.

## Analytics

- Google Analytics is configured through `_config.yml` with `google_analytics`.
- The tag is loaded conditionally in `_layouts/default.html`.

## Deployment Model

- This repo is intended to publish from the `main` branch.
- Local Docker is for development only.
- If deployment behavior changes, inspect repo settings and any CI configuration before editing build commands.

## Good First Checks Before Editing

```sh
git status --short
git branch --show-current
sed -n '1,200p' _config.yml
sed -n '1,220p' docker-compose.yml
```

## When Finishing Work

Before wrapping up:

1. Review the changed files.
2. Make sure no generated artifacts were accidentally edited.
3. If you ran Docker, stop it with `docker compose down` unless the user wants it left running.
