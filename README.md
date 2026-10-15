# Shivam Tiwari — Personal Website

**Live:** https://www.shivamtiwari.si/

> Served on a custom domain via GitHub Pages. `baseURL` in `hugo.yaml` must stay
> set to `https://www.shivamtiwari.si/` (with the trailing slash) and the same
> domain is committed in `static/CNAME`. If `baseURL` ever points at the old
> `.../personalwebsite/` project URL, asset paths resolve under that subpath and
> the live site renders unstyled on the custom domain.

A personal website built with [Hugo](https://gohugo.io/) and the
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, in the spirit of
[pulkitverma.net](https://pulkitverma.net/) and
[lilianweng.github.io](https://lilianweng.github.io/).

## Requirements

- Hugo **extended** v0.146.0 or newer. Install on macOS: `brew install hugo`.

## Local development

```bash
hugo server -D
```

Then open http://localhost:1313. The site hot-reloads as you edit.

Because `baseURL` is a bare domain (no subpath), `hugo server` serves the site at
the root of `localhost:1313`, exactly as it is served in production.

## Build for production

```bash
hugo --minify
```

The static site is generated into `public/`.

## Your profile photo (circular, LinkedIn-style)

Drop your photo at **`assets/images/profile.png`**, replacing the placeholder.
The theme automatically crops it into a circle, so you do not need to pre-crop it.
A square image (ideally 400x400 or larger) works best. To adjust the displayed
size, change `imageWidth` / `imageHeight` under `profileMode` in `hugo.yaml`.

## Editing content

| Page              | File                        |
| ----------------- | --------------------------- |
| Home (hero)       | `hugo.yaml` (`profileMode`) |
| About             | `content/about.md`          |
| Experience        | `content/experience.md`     |
| Projects          | `content/projects.md`       |
| Research & Speaking | `content/research.md`     |
| Blog posts        | `content/posts/*.md`        |

Add a new blog post:

```bash
hugo new content posts/my-new-post.md
```

Edit `date`, `title`, `summary` and `tags` in the front matter, then write in Markdown.
The post appears automatically at `/posts/` (linked from the "Writing" menu item).

## Before you publish — check these

1. **`baseURL`** in `hugo.yaml` and **`static/CNAME`** — both should read
   `www.shivamtiwari.si`. They must agree, or the deployed site breaks.
2. **Social links** under `params.socialIcons` — including the Google Scholar URL,
   which still has a placeholder `SHIVAM_SCHOLAR_ID` (also in `content/research.md`).
3. **Photo** — replace `assets/images/profile.png` (see above).

## Deploying (free options)

### GitHub Pages

1. Push this repo to GitHub.
2. Add a workflow at `.github/workflows/hugo.yaml` (see the
   [Hugo docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/)).
   Note: keep the PaperMod theme as a git submodule or the build will miss it.

### Vercel / Netlify

- Build command: `hugo --minify`
- Output directory: `public`
- Set the Hugo version to `0.146.0` or newer (extended).

## Theme

PaperMod is included as a git submodule in `themes/PaperMod`. To update it:

```bash
git submodule update --remote --merge
```
