# ACR Engineering Documentation (GitBook Source)

This repository is the source for the **ACR Engineering Documentation** GitBook, published at
[enigmatics.gitbook.io/dev-magang](https://enigmatics.gitbook.io/dev-magang).

<p align="center">
  <a href="docs/README.md"><img src="https://img.shields.io/badge/GitBook-Documentation-blueviolet?style=flat-square" alt="GitBook" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License" /></a>
</p>

## Repository Purpose

All content in `docs/` renders as the published GitBook. Changes committed to `main` are the source of truth for that publication — there is no separate publishing step in this repository itself.

## Directory Structure

```text
.
├── .gitbook.yaml      # GitBook configuration (root, landing page, navigation source)
├── SUMMARY.md         # Repository-level table of contents (points into docs/)
├── docs/              # GitBook documentation root (see .gitbook.yaml)
│   ├── README.md      # Landing page (GitBook `structure.readme`)
│   ├── SUMMARY.md     # GitBook navigation (GitBook `structure.summary`)
│   ├── introduction.md
│   ├── tech-stack.md
│   ├── architecture.md
│   ├── api/
│   ├── projects/
│   ├── components/
│   ├── development/
│   └── changelog.md
└── LICENSE
```

## Editing the Documentation

1. Edit the relevant file under `docs/` (keep Markdown lint-clean, consistent heading hierarchy, and correct relative links).
2. If you add a new page, register it in `docs/SUMMARY.md` — GitBook only surfaces pages that appear in the summary/navigation file for the `./docs` root.
3. Run `git commit` — GitBook picks up `main` automatically.

## Checking Navigation & Links

- `SUMMARY.md` (root) and `docs/SUMMARY.md` are mirrors of each other; keep both in sync.
- There is no package.json-based validator in this repo, so verify links manually or with an external tool (e.g., `markdown-link-check`) before pushing.

## Relationship to the Published Site

The published site at `enigmatics.gitbook.io/dev-magang` is generated from this repository via GitBook's built-in sync. Editing content here does **not** require a separate `gitbook publish` step in this repo.

## License

MIT — see [`LICENSE`](LICENSE).

## Author

- **Engineer:** Adi Cahyadi Ramadhan (EnigmaAura)
- **GitHub:** [@adicahyadir](https://github.com/adicahyadir)
