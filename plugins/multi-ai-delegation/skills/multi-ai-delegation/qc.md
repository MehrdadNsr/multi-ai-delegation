# Quality control

## 1. Mechanical checks (code, every chunk, on arrival)
- It parses (parse_chunk, workers/common.md 7); the header is exact; every row has the same column count; no stray prose.
- Every source_id exists in the input and inside the chunk's range (its canary ids included).
- CHECK lines match the rows actually returned; the ALL DONE ids match the input.
- Coverage: list input ids that got no row; they feed the false-negative sample in 2.
- Duplicates, empty required fields, values outside the allowed sets.
- Canary rows: compare them at once (3).
Fail: re-ask that chunk once, naming the problem; a second failure gets a fresh chat with a learned rule, a third re-routes it (modes/run.md 3, within lifecycle.md 11).

## 2. Spot-check against the source (Claude reads the raw items)
- Sample every row if there are 30 or fewer; otherwise max(20, 5%) random rows, capped at 60, plus 10 random ids that got no row. Record the seed and the ids checked.
- Tag each error: fabricated (not in the source) / wrong value / missed / format.
- Any fabricated row or invented id: reject the whole chunk and redo it elsewhere (lifecycle.md 11). More than about 5% wrong values in the sample: redo or cross-check that chunk. Otherwise fix what was found and report the rate. Tighten these thresholds when stakes are high.

## 3. Canary items
- When known answers exist (items Claude already verified, or an independent dataset with answers), mix 2-3 canaries into each chunk at random positions, each with a fresh id in the chunk's id style that no real item uses (e.g. numbers after the last real id). The ledger keeps which ids are canaries and their expected answers; the prompt never says which. The template's "Ids run from" line then names the first and last ids as they appear in the chunk.
- Never use personal data as canaries.
- A wrong or missing canary flags the chunk: spot-check every row of it, or redo it elsewhere (lifecycle.md 11).
- Remove canary rows before the merge. Report canary accuracy per worker and add it to the scorecard (state.md 5).

## 4. Cross-model check (high stakes: anything published or sent to an employer or official body, money, health, legal, irreversible decisions)
- Run the same chunk on a second worker from another family, independently and in parallel: neither sees the other's output, so there is no groupthink. Families on hand: OpenAI (ChatGPT), xAI (Grok), Google (Gemini, AI Studio, Gemini Notebook), DeepSeek, Moonshot (Kimi), Alibaba (Qwen), and whatever OpenRouter offers. Microsoft Copilot has run OpenAI models, so it is not an independent check on ChatGPT. Claude subagents are Claude's own family (Anthropic): never an independent check.
- Diff by source_id. Agreement: accept (still spot-checked). Disagreement: Claude decides against the source text, not by majority vote and not by which answer sounds better.
- When a model judges: give it the source and the candidate in spotlighting fences (templates.md 2), hide which model wrote what, swap the order in pairwise comparisons, use a coarse scale (pass/fail or 1-4), and require a source id behind every verdict. Judges favour their own family, the first position and longer answers, so never let a family be the only judge of its own output, and that includes Claude, or its subagents, judging Claude.
- Reasoning that sounds right but cannot be traced to the source is unverified: quarantine it rather than averaging it in.
- A high-stakes conclusion, Claude's own included, also gets a challenge pass before it is accepted (modes/review.md 2).

## 5. Merge
- Combine in id order; dedupe on source_id plus the key fields; drop the canary rows; add provenance columns (worker, chunk, verified yes/no).
- Keep real disagreements visible in the result; the synthesis must not invent consensus.
- Final completeness: every input id is either in the output or in an exclusions list with a reason.

_multi-ai-delegation · designed by Mehrdadnsr_
