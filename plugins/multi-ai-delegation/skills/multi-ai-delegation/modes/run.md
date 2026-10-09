# Run mode: bulk delegated work

For many independent items (chat exports, logs, transcripts, long PDFs): extraction, tagging, drafting or generation in chunks. lifecycle.md applies; this file adds the run-specific shaping (lifecycle.md 3.1) and step 6.

## 1. Shape
1. Shrink first with code: pre-filter, clean, dedupe; give every item a stable id (L0001, L0002... if it has none). Cost follows how much you send and in which mode, not how you chunk it.
2. Split into independent chunks with id ranges, each sized for its worker's window (limits.md).
3. Canaries (qc.md 3): when known answers exist, mix 2-3 canary items with fresh ids into each chunk. The ledger keeps which ids are canaries and their expected answers; the prompt never says which.
4. Prompts: templates.md 3 (extraction) with the run tag (templates.md 1); subagent briefs: workers/common.md 10.

## 2. Fire and poll
1. Pilot first (lifecycle.md 5).
2. Fire all prompts first, then poll round-robin; Chrome prompts go out before subagents are launched (workers/common.md 10).
3. Save each raw answer the moment it arrives, in the run folder, and log it in the ledger (state.md 2).
4. Validate each chunk on arrival; redo or re-route failures (qc.md 1, within lifecycle.md 11). Spot-check against the source; cross-model check when stakes are high (qc.md 2, 4).

## 3. Continue and retry
- PAUSED or no ALL DONE line: in the same chat send `Continue exactly from id NEXT_ID. Same format and same rules.` (one line with no comma, so it can be typed and never parses as a CSV row). At most 3 continues per chunk; then split it smaller.
- A chunk fails its checks (qc.md 1): re-ask it once in the same chat, naming the problem. Refusal or format drift: resend once with the OUTPUT block repeated at the end; that is the re-ask.
- The same chunk fails twice: open a new saved chat with the original prompt plus one short learned rule (templates.md 9). It counts as the chunk's second and last retry on that worker; a third failure re-routes it (lifecycle.md 11).

## 4. Merge
qc.md 5: combine in id order with the canary rows removed, provenance columns, and the final completeness check.

_multi-ai-delegation · designed by Mehrdadnsr_
