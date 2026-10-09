# Run state formats

The state lives outside the skill, never in these skill files (they are replaced on every update). Where it goes follows SKILL.md 0.2: memory when a memory tool is available; otherwise local files under ./ai-runs/; otherwise only this conversation (say so once). Procedures (when to write, mirroring, resume): workers/common.md 11.

## 1. Layout and run ids
- ai-runs/RUN/: chunk files, subagent briefs, raw answers (SITE-CHUNK.txt) and ledger.csv (where the folder lives: workers/common.md 11).
- ai-runs/status.md: with no memory tool, the run status (3) and the welcome flag line "welcome shown: DATE" (SKILL.md 0.1), in ./ai-runs/.
- ai-runs/recipes/NAME.md: saved recipes (4).
- ai-runs/scorecard.csv: the worker scorecard (5).
- Run id: <project>-<month><day>, plus a letter for a second run that day (survey-oct9, survey-oct9b).

## 2. Ledger (ledger.csv)
One row per chunk attempt: run, chunk, ids, site, tier, mode, chat URL or job id, prompts used, status, retries, file, verified, canary ids, canary result. The pilot is chunk "pilot"; a subagent's name or id goes in the chat URL column; a room without a readable URL (OpenRouter) gets its title.

## 3. Run status (memory, or ./ai-runs/status.md)
One paragraph per run: with a memory tool, in the memory file of the project the run serves (its /areas/ file) or in /areas/ai-runs.md, which also holds the welcome flag; with no memory tool, in ./ai-runs/status.md. It gives the run id and date, the approved plan in one line, chunks verified, chunks pending (site and chat URL each), where the files are, the next step. Replace that run's previous paragraph rather than appending; at the end shrink it to one line (done, where the report and files are). Memory rules apply (read first, version token, privacy): ids, counts, URLs and paths only, never content from the material. No store works or a write fails: say so and carry on.

## 4. Recipes
- When: after a job type succeeds once (all checks passed and the user accepted the result), save it as a recipe.
- Contents: name; job type; the worker prompt with everything filled in except the input; routing and modes; chunk size; checks (sample sizes, thresholds); canary sources (never personal data); learned rules and pitfalls from the run.
- Where: ai-runs/recipes/NAME.md in the user's run files (a connected folder, or ./ai-runs/ in Claude Code), or a short form in memory when neither exists.
- Reuse by name ("use the NAME recipe"): the plan starts from it, but the status check, the plan table and the user's go still apply. Update the recipe when a later run improves it.

## 5. Worker scorecard
- scorecard.csv (or a short table in memory when there are no run files): date, run, worker, model and mode, job type (extraction, tagging, generation, fact check), items, error rate in the spot-check, canary accuracy, minutes per chunk, cost (quota share or credits), notes. One row per worker per run.
- Routing reads it: among same-tier sites, route to the best record for that job type and say why in the plan (lifecycle.md 3.2). Few rows mean a weak record: say so rather than over-trusting one run.

_multi-ai-delegation · designed by Mehrdadnsr_
