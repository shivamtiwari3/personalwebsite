# Shivam Tiwari — Personal Website

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

## Build for production

```bash
hugo --minify
```

The static site is generated into `public/`.

## Your profile photo (circular, LinkedIn-style)

Drop your photo at **`static/images/profile.png`**, replacing the placeholder.
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
| Speaking / OSS    | `content/speaking.md`       |
| Contact           | `content/contact.md`        |
| Blog posts        | `content/posts/*.md`        |

Add a new blog post:

```bash
hugo new content posts/my-new-post.md
```

Edit `date`, `title`, `summary` and `tags` in the front matter, then write in Markdown.
The post appears automatically at `/posts/` (linked from the "Writing" menu item).

## Before you publish — update these

1. **`baseURL`** in `hugo.yaml` — set it to your real domain, e.g. `https://shivamtiwari.com/`.
2. **Social links** under `params.socialIcons` and in `content/contact.md` — the
   GitHub and X URLs are placeholders, swap in your real handles.
3. **Photo** — replace `static/images/profile.png` (see above).

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
