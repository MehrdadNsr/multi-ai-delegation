# Contributing

Thanks for helping. A few rules keep the skill reliable and safe.

## Before a pull request

- Live-test every site you touch: run "test" on it, and for routing, parsing or prompt changes, a small real job. Say in the pull request what you tested, where (claude.ai, the desktop app or Claude Code) and when.
- Date every figure you add to limits.md or gaps.md (YYYY-MM-DD), with a source link or "observed".
- No personal data in files, issues, pull requests or screenshots: no emails, account names, chat URLs or ids, chat titles from sidebars, credit amounts or private material.
- Keep the attribution lines: the version line under the title of SKILL.md and the last line of every skill file.
- Keep the skill files in English; users get their own language through their profile.
- Keep instructions short and plain: Claude reads them on every run.

## Release checklist

1. Bump the version everywhere the docs require, in one commit: `version` in `plugins/multi-ai-delegation/.claude-plugin/plugin.json` and the version line in SKILL.md, with the same number. Don't add a version to the plugin entry in `.claude-plugin/marketplace.json`: plugin.json wins and the validator warns.
2. In the same commit, add a line to both CHANGELOG.md files (the repository root and the skill folder).
3. Run `claude plugin validate .` from the repository root.
4. Push. Installed copies stay on their cached version until the version string changes, so a release without a bump never reaches users.
