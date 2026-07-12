# AGENTS.md

Instructions for AI agents (Codex, Claude, etc.) working in this repo. Read this before making changes.

## What this repo is

Study repo for **Linear Algebra for Machine Learning and Data Science** (DeepLearning.AI, Course 1 of the Mathematics for Machine Learning and Data Science Specialization, instructor Luis Serrano). Notes, notebooks, and problem sets. Author: Stephen D. Gardner.

## Layout

| Path | Contents |
|------|----------|
| `notes/` | Written notes and module summaries (markdown, math in LaTeX) |
| `notebooks/` | Jupyter notebooks: labs, experiments, worked examples |
| `problem-sets/` | Practice problems and solutions |
| `resources/` | Cheatsheets, references, datasets |
| `Deeplearning.ai_Linear Algebra/` | Course materials (currently a placeholder) |
| `Gardner_Linear Algebra Certificate.pdf` | Course completion certificate |

Empty scaffold folders hold a `.gitkeep`.

## Hard rules

- **NO EM-DASHES or EN-DASHES, EVER.** Do not use the `—` (em-dash) or `–` (en-dash) character in ANY output: prose, code comments, commit messages, docs, notes, filenames. Plain hyphens (`-`) are fine. Use commas, colons, or parentheses instead. This is a firm, non-negotiable preference of the repo owner.
- **Git: push to BOTH `main` and `master`.** The remote keeps both branches in sync. After committing:
  ```bash
  git push origin main
  git push origin main:master
  ```
  Confirm with `git ls-remote origin main master` (both refs should match).
- **Discuss before executing.** Propose the plan and get a green light before making non-trivial changes. Do not push unless asked.

## Conventions

- **Document formatting default:** Times New Roman, 12pt, page numbers right-aligned (only when multi-page).
- **Commit messages:** clear and plain, no em-dashes. Do not add AI co-author trailers unless the owner asks.
- **Remote:** SSH (`git@github.com:stephengardnerd/linear-algebra-ml-ds.git`). Push over HTTPS is broken on this machine (dead Intel credential helper), so SSH only.
- **`gh` CLI** is installed and authenticated as `stephengardnerd` with `repo` scope. Use `gh repo edit` for the GitHub About/description, `gh api` for uncached reads (the public REST endpoint is CDN-cached and lags edits).

## Notes-to-PDF pipeline (no pandoc / TeX installed)

Math-bearing notes are authored as markdown with LaTeX `$...$`. To produce a readable PDF:

1. Write a self-contained HTML file: Times New Roman body, MathJax v3 `tex-svg` from CDN, table styled with light borders. **Set `svg: { fontCache: 'none' }`** in the MathJax config; the default `'global'` appends a hidden font-cache element that forces a phantom blank trailing page in Chrome print.
2. Render with headless Chrome (installed at `/Applications/Google Chrome.app/Contents/MacOS/Google Chrome`):
   ```bash
   "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
     --headless=new --disable-gpu --no-pdf-header-footer \
     --virtual-time-budget=20000 \
     --print-to-pdf="out.pdf" "file:///abs/path/to/page.html"
   ```
   `--virtual-time-budget` gives MathJax time to typeset before capture.
3. Verify without extra installs: page count via `mdls -name kMDItemNumberOfPages -raw out.pdf`; rasterize page 1 for a visual check via `qlmanage -t -s 1400 -o <dir> out.pdf` (poppler is NOT installed, so `pdftoppm` is unavailable).

See `notes/notations.md` (source) and `notes/notations.pdf` (output) for a working example.

## Environment

- macOS (Darwin). `python3` at `/Users/Mach15/opt/anaconda3/bin/python3`. `brew` available at `/usr/local/bin/brew`.
- No pandoc, no LaTeX, no poppler, no wkhtmltopdf. PDF path is the headless-Chrome + MathJax pipeline above. If you need a one-liner instead, `brew install pandoc basictex` (ask first).
- Note: the repo folder was renamed from `...Data Science & Machine Learning` to `...Data Science and Machine Learning` (the `&` broke a tooling path). If a local config references the old path, that is why.
