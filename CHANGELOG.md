# Changelog

## 1.1.0

- Add `to-question`, renamed from `to-questionnaire`: drafts a questionnaire for another person instead of asking the user the recipient's questions.
- Narrow the `grill-me` and `to-question` descriptions so an interview request and a questionnaire request each reach the right skill.
- `handoff` can suggest `to-question` when someone else must supply facts.
- Update the plugin manifests and the English and Korean READMEs for four skills.

## 1.0.0

- First release of Clarity Toolkit for Claude with three skills: `grill-me`, `meta-conv-filter`, and `handoff`.
- `grill-me` keeps interviewing in rounds until the user wants to converge, instead of switching to building early.
- `handoff` can resume work from a supplied handoff and treats it as context to verify.
- `meta-conv-filter` runs only on request or for a clean final version, not on ordinary chat replies.
- Each skill is self-contained: no shared files, templates, or scripts are required.
- Includes a Claude Code plugin manifest and marketplace file.
