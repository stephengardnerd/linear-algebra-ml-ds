# Handover

**Date:** 2026-07-12
**From:** Claude (Opus 4.8, Claude Code)
**To:** Codex
**Repo:** `linear-algebra-ml-ds` (Linear Algebra for ML and Data Science, DeepLearning.AI Course 1)

Read `AGENTS.md` first for the durable rules and the notes-to-PDF pipeline. This file is a point-in-time snapshot.

## Current state

- Latest commit: `258fa42` "Add Notations reference to notes (markdown + PDF)".
- `main` and `master` both point at `258fa42` on the remote. Working tree clean (before this handover commit).
- Only `notes/` has real content so far (`notations.md` + `notations.pdf`). `notebooks/`, `problem-sets/`, and `resources/` are still empty scaffolds (`.gitkeep` only).
- Progress checkboxes in `README.md` (Weeks 1 to 4) are all still unchecked.

## Done in the last session

1. Made "no em-dashes" a hard rule (now in the owner's global config and echoed in `AGENTS.md`). Plain hyphens are fine; em/en dashes are not.
2. Fixed the GitHub About/description: replaced an em-dash with a plain hyphen. Live value confirmed via `gh api`.
3. Added `notes/notations.md` (the DeepLearning.AI Course 1 notation table, transcribed to LaTeX math) and a single-page `notes/notations.pdf` (Times New Roman, MathJax-typeset). Committed and pushed to both branches.

## Suggested next steps (not started, owner to prioritize)

- Save the raw "Notations" screenshot into `resources/` as a visual backup, if wanted.
- Start **Week 1** notes (Systems of linear equations) in `notes/`.
- Build topic notebooks in `notebooks/` (e.g. solving linear systems, row reduction, dot products, determinants, eigen decomposition into PCA).
- Populate `problem-sets/` and tick the README progress boxes as weeks are completed.

## Gotchas to carry forward

- **Push to both `main` and `master`** every time (see `AGENTS.md`).
- **No em/en dashes** in anything.
- **PDF pipeline quirk:** MathJax `fontCache: 'none'`, or Chrome print emits a phantom blank second page.
- **Ask for a green light** before non-trivial changes; do not push unless asked.
