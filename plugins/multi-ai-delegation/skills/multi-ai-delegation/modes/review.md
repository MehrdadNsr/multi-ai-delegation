# Review mode: review chain, challenge pass, second opinion

lifecycle.md applies (no pilot unless the material is chunked). Workers come from families other than the producer's, never Claude subagents for Claude's own work, subscriptions first (fast mode).

## 1. Review chain (a draft, plan, code or document)
1. Worker A lists issues, each with a confidence label (high / medium / low), a location and a severity guess (templates.md 7, A).
2. Worker B, from another family, gets the same material plus A's list inside spotlighting fences (templates.md 2); it confirms or rejects each issue, with a reason, and adds what A missed (templates.md 7, B).
3. Claude checks every issue against the material and merges one ranked list, critical to minor, keeping who found what (A, B or both) and B's verdicts. Issues Claude rejects stay listed with the reason.

## 2. Challenge pass (any high-stakes conclusion, Claude's own included)
Before accepting it, a worker from another family argues against it (templates.md 8). Claude answers each objection against the evidence: accepted (the conclusion changes), rejected (with the reason) or open. The report says which objections changed the result. High stakes: as in qc.md 4.

## 3. Second opinion and checking
- Second opinion, judge or devil's advocate on a plan, draft or idea: templates.md 5. Grok is a good contrarian but tends to mirror the framing it is given.
- A worker as checker of claims or rows against a source: templates.md 4; judge rules: qc.md 4.
- Every prompt in this mode follows neutral framing (SKILL.md 2.10): no preferred answer in the prompt, the author hidden, the angle named in the report. When the user disputes a conclusion, revisit its evidence; never recruit another worker's agreement to settle it.

_multi-ai-delegation · designed by Mehrdadnsr_
