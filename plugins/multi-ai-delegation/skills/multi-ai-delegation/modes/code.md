# Code mode: a coding agent the user drives (Antigravity)

Repo-level coding (a multi-file change, run and test) goes to the user's coding agent. Claude cannot drive the Antigravity desktop app from Chrome, so Claude writes the brief, the user runs it, and Claude reviews the result. lifecycle.md applies (the plan has one row for it).

1. Claude writes one self-contained brief in a single code block with nothing written under it; the user pastes it into a new Antigravity agent task. If the profile names a brief skill for the project, follow its structure (a brief written for Claude Code or Codex carries over).
2. The brief holds: goal; context (repo, stack, key paths); scope and non-goals; constraints (no new dependencies without asking, keep tests green, no secrets in code, no destructive commands); acceptance criteria with the exact commands or tests that prove them; deliverables (changes on a branch, implementation plan and walkthrough artifacts, test output); a stop rule (blocked or ambiguous: stop and report instead of guessing).
3. Suggest Planning mode for anything beyond a small fix (Fast mode skips the plan) and the artifact review policy "Request Review", so the user approves the plan before code changes.
4. Standing rules belong in the repo, not in every brief: workspace rules in `.agents/rules/` (the older `.agent/rules/` is still read), global rules in `~/.gemini/GEMINI.md`, repeatable procedures as Workflows run with `/workflow-name`. Each rules file is limited to 12,000 characters.
5. Return path: the user brings back the plan or walkthrough and the diff (or the branch name if Claude can reach the repo). Claude checks every acceptance criterion, the test results, scope creep and risky changes, then writes the follow-up brief if one is needed.

_multi-ai-delegation · designed by Mehrdadnsr_
