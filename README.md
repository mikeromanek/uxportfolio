
# UX Portfolio (uxportfolio)

This repository contains a simple personal portfolio website built with plain HTML, SCSS, and compiled CSS. It is intended to be published using GitHub Pages.

## What’s included
- `index.html`, `about.html`, `projects.html`, `contact.html`, `thank-you.html` — site pages
- `styles.scss` — source SCSS file
- `styles.css` — compiled CSS (the site expects this at the project root)
- `styles.css.map` — source map for debugging styles
- `images/` — project images and assets

## Quick local preview
1. Open `index.html` in your browser from the project root. No server is required for a simple HTML/CSS preview.
2. If you use SCSS and want to compile locally, install Dart Sass or use `npx`:

```powershell
# Compile once
npx sass styles.scss:styles.css

# Watch for changes (rebuild on save)
npx sass --watch styles.scss:styles.css
```

When you compile, `styles.css` will be written in the repo root (the HTML pages link to `styles.css`). If you prefer to keep build artifacts out of the repo, see the GitHub Actions section below.

## Git & GitHub (publish to Pages)

Recommended flow to publish to GitHub Pages from the `main` branch (root):

1. Create or use a GitHub repository (e.g., `mikeromanek/uxportfolio`).
2. Add the remote to your local repo (run from project root):

```powershell
git remote set-url origin https://github.com/<your-username>/<repo>.git
git push -u origin main
```

3. On GitHub: go to your repo → Settings → Pages. Set Source: `main` / `/(root)`. Wait a minute and open the published URL shown there.

Notes:
- Make sure `index.html` and `styles.css` are present at the repository root (not inside a subfolder) because Pages will serve the root.
- If your repo already had an initial commit (for example a README), you might need to merge or force-push; see the Troubleshooting section.

## Continuous build (optional): compile SCSS on push using GitHub Actions
If you prefer not to commit `styles.css`, you can add a GitHub Actions workflow that compiles `styles.scss` to `styles.css` on push and commits the built file back to the `main` branch.

Suggested workflow file path: `.github/workflows/compile-scss.yml` (create this file in the repo). The workflow would:
- Install Node
- Run `npx sass styles.scss:styles.css`
- Commit and push the generated `styles.css` back to `main`

If you'd like, I can add this workflow for you.

## Troubleshooting
- 404 on GitHub Pages: confirm Pages source is `main / (root)` and `index.html` exists at repo root.
- `git push` rejected: the remote contains commits you don’t have locally. Use `git pull --allow-unrelated-histories` to combine histories, or force-push if you intentionally want to overwrite remote.
- OneDrive sync: this repo lives inside OneDrive. OneDrive can cause file-locks or delayed sync. For active development, consider moving the repo to a non-synced folder like `C:\Users\<you>\Projects\uxportfolio`.

## Contact / next steps
- If you want, I can:
	- Finish wiring a GitHub Actions workflow to build SCSS on push.
	- Help push your local branch to the GitHub repo and finish enabling Pages.
	- Move build outputs or change how CSS is served.

Reply with which of those you'd like me to do next and I will continue.

---
_Last updated: 2025-09-25_
