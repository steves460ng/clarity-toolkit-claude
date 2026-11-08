# Changelog

## 1.0.0

- First release of Clarity Toolkit for Claude with three skills: `grill-me`, `meta-conv-filter`, and `handoff`.
- `grill-me` keeps interviewing in rounds until the user wants to converge, instead of switching to building early.
- `handoff` can resume work from a supplied handoff and treats it as context to verify.
- `meta-conv-filter` runs only on request or for a clean final version, not on ordinary chat replies.
- Each skill is self-contained: no shared files, templates, or scripts are required.
- Includes a Claude Code plugin manifest and marketplace file.
