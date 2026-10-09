# Lifecycle (every mode)

Every mode runs these steps in order; the mode file (modes/) supplies step 6 and its own shaping. "Plan only" stops after step 3; "status" is step 2 alone; "test" runs steps 1-4, then one canary prompt per site (modes/test.md). Always-on rules (tiers, gate, money, privacy, safety, language): SKILL.md 2.

## 1. Extension check (first, in every mode)
Load the Claude in Chrome tools and call tabs_context_mcp (workers/common.md 1). A missing tool, an error or no response means the extension is not connected. Then stop all browser work and give these steps in the user's language:
1. Install the "Claude" extension from the Chrome Web Store (the official listing by Anthropic).
2. Sign in with the same Claude account.
3. Pin it to the toolbar.
4. Keep Chrome open while a run lasts.
5. Allow each site the first time Claude uses it.
6. In Claude Code: start a session with `claude --chrome`, or run `/chrome` to connect (extension version 1.0.36 or later).
Meanwhile offer only routes that need no browser: Claude alone, Claude subagents, MCP-connected tools such as Higgsfield, and relay mode (workers/common.md 9). Check again once the user says it's done.

## 2. Status check
Without sending any prompt, check each worker: signed in (workers/common.md 3, step 2), extension permission for its site, and the visible quota or credit meter with its reset time (the Meter line of each worker file; Higgsfield: its credits tool; subagents: the Claude usage page). Reply with a small table in the user's language: Worker | Signed in | Permission | Meter and reset | Note. The "status" command checks every worker; at the start of every plan, check the workers the plan may use, the fallback included. A logged-out worker: say so, and when the profile names a Google sign-in account, offer the sign-in in the plan (workers/common.md 3, step 2). Close the tabs it opened.

## 3. Plan

### 3.1 Shape the job
1. Define the deliverable and its acceptance checks. Planning, judgment, merging and final wording stay with Claude.
2. Keep with Claude: short questions and quick back-and-forth, where the browser round trip costs more than it saves (except one quick question the user directs to a named Tier 1 or Tier 2 site, asked without the gate); anything workspace code can do (filter, dedupe, count, convert, validate), always tried first because it is exact and free; acting in the user's accounts beyond chatting (sending messages, buying, changing settings, connecting apps), where credit-spending generation in a media tool is the one exception, only through SKILL.md 2.3-2.4. For bulk work with a direct API route to the model, prefer the API to web UIs (exact input and output, no page fragility).
3. Shape the rest as the mode file says (chunks and ids, council stances, the review chain).
4. A saved recipe for this job type (state.md 4)? Start from it; the status check, the plan table and the go still apply.

### 3.2 Route
Route each piece to the lowest tier that can do it (SKILL.md 2.2; the user's tiers: the profile, SKILL.md 0.2). Among same-tier sites, route to the best scorecard record for that job type (extraction, tagging, generation, fact check) when its quota allows, otherwise to the most quota left, and say why in the plan, e.g. "ChatGPT: fewest errors in the last two extraction runs" (state.md 5). Route by job fit, tier and quota left, not by leaderboard rank (model snapshot: limits.md).

| Sub-task | Send to (mode) | Why |
|---|---|---|
| Plan, split, judge, merge, final wording; anything needing the user's private context | Claude | Holds the full picture; private context stays here |
| Filter, dedupe, count, convert, validate | Claude + Python | Exact and free; do it before delegating |
| Generation, drafting, extraction or tagging over material already here | Claude subagents (Haiku or Sonnet) | Parallel, no page fragility; same family as Claude, so never the independent check |
| Bulk extraction or tagging into a strict CSV | Subagents when the Claude quota allows; otherwise, or alongside them, ChatGPT (Instant) and Grok (Fast or Auto) in parallel, splitting the chunks | ChatGPT and Grok kept a strict format exactly in the test; largest fast quotas (limits.md) |
| Same, public non-personal text, quotas tight | DeepSeek (DeepThink and Search off); Kimi or Qwen as further backups | Free; all three passed the test; Chinese jurisdiction, so public text only |
| Live news, what people are saying on X | Grok (Auto) | Native real-time X and web search |
| One huge file or text | AI Studio (default Flash; Pro only if needed), Gemini app second; Kimi or Qwen for public text when those quotas are out | Long context, live token count; unpaid-service terms, so no personal data |
| Long video, YouTube link | Gemini (Flash first, Pro if needed); on a free plan, AI Studio for public material | Multimodal; 1M-token context on paid Gemini plans and in AI Studio |
| Code run on a file uploaded there | ChatGPT | Its code sandbox |
| Questions answered from documents the user adds (papers, reports), with citations | Gemini Notebook (NotebookLM) | Answers only from its sources and cites them; not for strict CSV (citation markers) |
| Quick fact check or current info with citations | Grok, ChatGPT or Gemini search (default search mode) first; Perplexity when those quotas are tight, as an independent second check, or when the user names it | Open the cited pages for anything that matters |
| Hard reasoning with a checkable answer (math, logic, tricky code) | ChatGPT Thinking; DeepSeek DeepThink when that quota is tight | Then verify with code or tests, never on trust |
| Multi-source research report | Claude; Gemini Deep Research or ChatGPT deep research as an independent second pass | Check citations either way |
| Wide many-model comparison | ChatGPT, Grok and Gemini side by side, Copilot as one more view (not independent of ChatGPT; untested, workers/copilot.md); AI Studio Compare mode for Gemini variants; OpenRouter ":free" models for more families (paid ones only if the user approves) | OpenRouter puts many families in one room, but it is Relay-only for now and its free models failed the test |
| Opposing views on a question or decision | Council (modes/council.md) | Stances for, against and neutral from three families |
| Second opinion, judge, devil's advocate, review chain, challenge pass | A family other than the producer's, never Claude subagents, subscriptions first (fast mode) (modes/review.md) | Avoids self-preference (qc.md 4); Grok is a good contrarian but tends to mirror the framing it is given |
| Images, video | The tool the user names; otherwise both in the plan: Higgsfield MCP with a quote, Gemini or ChatGPT when they can (modes/media.md) | The user downloads the files; Higgsfield: one retry, then stop and report |
| Music | Suno | A Tier 3-only job; the user downloads the files |
| Voice, narration, a presenter voice | ElevenLabs, consented voices only | A Tier 3-only job; the user downloads. Stock-voice narration may also work in AI Studio's speech mode (untested): offer it |
| Repo-level coding (multi-file change, run and test) | The coding agent the user drives (e.g. Antigravity in Planning mode; modes/code.md) | Claude writes the brief and reviews the result |

### 3.3 Estimate (before anything is sent)
"Big" = more than about 5 prompts to one site, any Thinking / Expert / Pro / Deep Research use, any upload, or any Tier 3 use; read the meters before and after a big run.
1. Measure what you will send after pre-filtering: items and characters. Rough tokens: English chars / 4; non-Latin scripts chars / 3 (can be off by 50%).
2. Prompts per site = the pilot + chunks + expected "continue" turns + retries, plus about 20%.
3. Size each prompt for the worker's window (limits.md); missing ids in the output mean it was too big (qc.md 1 catches it).
4. Compare with the limits snapshot (limits.md) and the site's own meter. Take each quota's reset time from the live meter, not from fixed cycles (the worker files say what each site shows), and spread a big run across the windows the meters show.
5. Use the cheapest mode that can do the job: extraction and tagging = Instant / Fast / Auto; Thinking / Expert / Pro only for sub-steps that need reasoning, on the smallest scope. After a big run, add the observed cost and times to the scorecard (state.md 5) and to the report (for the calibration log in limits.md, which only changes upstream).

### 3.4 Plan table
Columns, in order (render them in the user's language, or with the profile's own headers when it has them): Site | Tier | Mode | Chunks (id ranges) | Volume per site (items + characters, rough tokens) | Prompts incl. continues and retries | Quota share or cost (credits/USD) | Est. time.
- One row per site, Claude (Tier 0) and any subagents (Tier 0b) included; a subagent row gives the number of agents, chunks per agent, model and a rough share of the user's Claude usage, and says plainly when the run could take a large share. Planned cross-checks get their own rows. Flag any site pushed past about half of a weekly quota, and never plan a site past its careful-mode daily cap (SKILL.md 2.9; today's counts: state.md 3): move the excess elsewhere or to another day and say so under the table.
- Time: rough wall-clock per site, about 1 min per chunk in fast modes, 3-10 min in reasoning modes, subagents about 1-3 min per chunk, plus polling (calibrate in limits.md). Sites run in parallel, so the total is about the pilot round plus the slowest site plus Claude's checks and merge. Claude's own work is timed by SKILL.md 2.8.
- Under the table: the total (prompts, volume, time) and the fallback site if one runs out; for each Tier 3 row, why nothing cheaper works and its estimated credits or USD (limits.md; Higgsfield: get_cost per job, plus one possible retry); a storage line: where the run files go (a connected folder; ./ai-runs/ in Claude Code; or a warning that results live only in the temporary workspace; workers/common.md 11); a sign-in line, when the status check found a worker logged out and the profile names a Google sign-in account: which sites Claude will sign in to with Google, and as which account; a personal-data line, "Personal data: none" or what goes where. Total over about 15 minutes: say the user needn't wait, e.g. "No need to wait; the report will be ready when you're back", and with Chrome workers add that Chrome must stay open and the computer awake.
- End with a short question, e.g. "Go?", or, with a Tier 3 row, its site and amount, e.g. "Suno about 20 credits (2 generations, 4 songs): spend it?".
- Plan only: stop here; nothing is sent.

Worked example (rendered in the user's language at run time):

| Site | Tier | Mode | Chunks (id ranges) | Volume per site | Prompts | Quota share or cost | Est. time |
|---|---|---|---|---|---|---|---|
| Claude (here) | 0 | - | pre-processing, QC, merge | all | - | free | about 10 min |
| Claude subagents | 0b | Sonnet | L0001–L0400 (1 pilot + 2 agents, 1 chunk each) | 400 items, 80k chars, about 20k tokens | 1 pilot + 2 + 1 retry = 4 | Claude quota; uncalibrated, probably a few % of a 5-hour session | about 3 min |
| ChatGPT | 1 | Instant | L0401–L0800 (1 pilot + 2 chunks) | 400 items, 75k chars, about 19k tokens | 1 pilot + 2 + 1 continue + 1 retry + 1 spare = 6 | about 4% of the 3-hour cap | about 4 min |
| Grok | 1 | Fast | L0801–L1200 (1 pilot + 2 chunks) | 400 items, 75k chars, about 19k tokens | 6 | about 4% of the weekly quota | about 4 min |

"Total: 16 prompts, 1,200 items, 230k characters (about 58k tokens), about 20 minutes (pilot round + slowest site + checks and merge). If one runs out: DeepSeek (Tier 2, public text only). Storage: only this chat's temporary workspace; connect a folder to keep the files. Personal data: none. No need to wait; just keep Chrome open and the computer awake; the report will be ready when you're back. Go?"

## 4. The go
Start only on a clear go ("go" or the user's word for it; the profile may list it). A go covers Tier 3 spend and personal data only as SKILL.md 2.3 says. If the user swaps or removes sites ("Grok has no credit left, give its chunks to ChatGPT"), re-plan, show the new table and wait again.

## 5. Pilot (chunked work)
After the go, send each worker one pilot chunk, the start of its range (about 5% of its items, at least 10; its rows count). Run the qc.md 1 checks and a quick qc.md 2 spot-check on it; only then fire the rest, with the time estimate rescaled by the pilot's measured times (SKILL.md 2.8). A failed pilot: fix the prompt and pilot once more, or re-route (11), before spending the rest of the quota.

## 6. Execute
The mode file. Drive sites per workers/common.md and the workers/SITE.md files in the plan; subagents per workers/common.md 10. Save each raw answer the moment it arrives, in the run folder, and log it in the ledger (state.md 2).

## 7. QC
qc.md: mechanical checks on arrival, the spot-check, canaries, and for high stakes a cross-model check (qc.md 4) and a challenge pass (modes/review.md 2).

## 8. Merge
qc.md 5, plus the mode file's merge notes.

## 9. Report
In the user's language; a long report goes in an HTML artifact (right-to-left for languages that need it). The plan table comes before the run; this report after it. Cover:
- Who did what: site, tier, model, sub-task, chunks and prompts, mode, quota seen (meter before and after when there is one); subagents with their number and model.
- Pilot results per worker: passed, or what was fixed or re-routed before the rest went out.
- Spend: for every Tier 3 site (Higgsfield included), the credits shown before and after and the actual spend (USD when known), next to the approved estimate or the one-line quote.
- Changes from the approved plan: chunks moved between approved sites, and any pause for the user's approval.
- What was verified and how: mechanical checks, spot-check sample size and error rate per worker, canary accuracy per worker, cross-model agreement rate, and which challenge objections changed the result. What is NOT verified, said plainly, plus anything redone or re-routed.
- Chats left in each site's history (every delegated chat is saved), with run tags and URLs: the chat sites' chats, Gemini Notebook notebooks, OpenRouter rooms in this browser, generations waiting in Suno, ElevenLabs or Higgsfield. Claude deletes none of them.
- Where the output and run files are (connected folder, or only the temporary workspace) and which the user must download; where the run status is kept (SKILL.md 0.2); one next step if there is one.
- For the maintainers, when there is any: what the run settled or found about a site (gaps.md, limits.md), dated, ready for an issue or pull request.

## 10. Save run state
After the pilot, after each batch of chunks, and at the end: raw answers and the ledger in the run folder (mirrored to the connected folder) and the run status in the state store (SKILL.md 0.2), in the state.md formats (procedure: workers/common.md 11). At the end, also add each worker's measured accuracy, speed and cost to the scorecard (state.md 5), and if this job type succeeded for the first time, save it as a recipe (state.md 4).

## 11. Mid-run changes
When a site hits its limit or fails, or a chunk must move:
- between sites in the approved plan, the named fallback included (Tier 0-2): go ahead and report it at the end; Claude (Tier 0) can always take a chunk back;
- to a site not in the approved plan (more subagents than approved included), to any Tier 3 site, or past an approved Tier 3 estimate: pause that chunk and tell the user first; the other workers keep going.

## 12. Kill switch
"stop", or its equivalent in the user's language (the profile may list the user's words), halts all sending at once: no new prompt, continue, retry, generation or subagent goes out. Then read and save what has arrived (partial answers marked partial; answers still generating stay in their saved chats for a resume), update the ledger and the run status, and report what's done, what's pending (with chat URLs) and what was spent. Subagents already running finish their current call, and nothing new is launched; generation jobs already submitted can't be recalled, so report them.

_multi-ai-delegation · designed by Mehrdadnsr_
