# Limits, costs and sources (volatile)

Read when filling the plan table (lifecycle.md 3.3-3.4). Every figure here is dated and changes often: prefer the live meters (the Meter line of each worker file). After every big run, report the observed cost and times, and any figure the run proved wrong, so the user can send them upstream as an issue or pull request (this file is replaced on every update). The user's own plans: their profile (SKILL.md 0.2).

## Prompt sizing (2026-10-08)
Size each prompt for the worker's window (rough, unverified for 2026): ChatGPT Plus default model up to about 40k characters of input per prompt (its chat window is reportedly ~32K tokens); Grok and DeepSeek up to about 80k; Gemini and AI Studio far more (AI Studio keeps a running token count by the composer); Kimi and Qwen untested beyond a tiny prompt. Missing ids in the output are the sign a prompt was too big; qc.md 1 catches it.

## Quota resets (2026-10-09)
Take reset times from each site's live meter, not from fixed cycles, and spread big runs across the windows the meters show (lifecycle.md 3.3):
- Gemini: officially refreshes every 5 hours up to a weekly cap.
- ChatGPT: shows when an allowance resets once a limit is hit; there is no fixed published Plus cycle.
- Grok: one weekly pool, which can reset early and unannounced.
- Claude (subagents): a rolling 5-hour session limit plus weekly limits (claude.ai Settings > Usage).

## Tier 3 cost estimates (2026-10-08)
Suno: about 10 credits per generation, which makes two songs; ElevenLabs: about 1 credit per character on Multilingual v2, 0.5 on Flash/Turbo; OpenRouter paid models: tokens times the model's listed price; Higgsfield: get_cost per job, plus one possible retry.

## Calibration log
- Grok Expert used about 18% of one account's weekly Grok quota to extract two weeks of a chat export (Oct 2026; plan unclear).
- Higgsfield quoted 35 credits for one default seedance_2_5 video (get_cost, Oct 2026).
- Two-worker council test (2026-10-09, about 630-character prompts): ChatGPT Instant answered in under 10 s; Grok Fast showed "Worked for 9s", and its answer rendered only after screenshot nudges in a background tab (about 30 s in all).
- Claude's own pace (2026-10-09, one model): a 27-file, 110k-character skill restructure with scripted diff checks and live browser tests took about 30 min against a 1.5-2 h estimate; every per-step estimate ran 4-5x long because Claude estimated at a person's pace and never rescaled mid-task. Measured: file writing about 10k characters a minute; scripted checks about 4-5 min; a status check of 13 known sites about 2 min; a two-worker prompt round about 3 min. Rules: SKILL.md 2.8.
- Read the meters before and after every big run and report the observed cost, each run's pilot result, minutes per chunk per site and the subagents' share of Claude usage, so this log can grow upstream and calibrate the time column and the 0b row (the user's scorecard keeps them too, state.md 5).

## Limits snapshot (Oct 2026; providers change these often)

| Service and plan | Limit shape |
|---|---|
| ChatGPT Plus | About 160 messages per 3 h on the default model, then a mini fallback; manually picked Thinking up to about 3,000 per week; about 80 uploads per 3 h. Unverified third-party figures: OpenAI publishes no fixed Plus cycle |
| Grok | Paid plans share one compute-based weekly pool (since Jun 2026) that can reset early and unannounced; the free tier has its own limits and fewer modes; Expert drains the pool fast. Sep 2026 sources tie the weekly % meter to paid tiers such as SuperGrok Lite |
| Gemini (Google AI Pro) | Compute-based: refreshes every 5 h up to a weekly cap; AI Pro = 4x standard; 1M-token context; when it runs out, chat continues on Flash-Lite; free plans get lower limits |
| DeepSeek (free) | No published web cap; "server busy" under load; DeepThink is slower |
| Google AI Studio (unpaid service, no billing) | Free-tier rate limits, not shown in the UI; a running token count shows by the composer; uploads wait until the user accepts the one-time media terms |
| Gemini Notebook (Google AI Pro) | An in-app notice said usage limits reset every 5 h (unverified); source and query caps not checked |
| Perplexity (free) | About 5 Pro searches a day, unlimited quick searches, 3 uploads a day (Jul 2026 source) |
| Kimi, Qwen (free) | No published web caps found; both answered the test within seconds |
| OpenRouter | ":free" models: 50 requests a day, 1,000 a day once at least 10 credits have been bought; paid models are billed per token |
| Suno (Pro) | 2,500 credits a month; about 10 credits per generation, which makes two songs; downloads capped at about 20 a month since Sep 2026 (the account page shows "Downloads Remaining"; extra downloads are sold, never buy them); songs made on a paid plan carry commercial rights |
| ElevenLabs (Free) | 10,000 credits a month; about 1 credit per character on Multilingual v2, 0.5 on Flash/Turbo; the Free plan has no commercial license |
| Higgsfield (via MCP) | Quote every job with get_cost (one default seedance_2_5 video: 35 credits) |
| Claude subagents | The same pool as the chats and Claude Code: a rolling 5-hour session limit plus weekly limits, and a separate weekly limit for some models (claude.ai Settings > Usage, 2026-10-09); each agent keeps its own context, so parallel agents use several times the tokens of one session (one guide: agent teams about 7x); no cost per chunk measured yet |

## Model snapshot (Oct 2026; verify, it changes monthly)
ChatGPT GPT-5.x (Instant / Thinking), Grok 4.x, Gemini 3.x (Flash / Pro; AI Studio's default was Gemini 3 Flash Preview), DeepSeek V4, Kimi K3, Qwen3.7-Plus; OpenRouter's free list changes often. Route by job fit, tier and quota left, not by leaderboard rank.

## Sources (checked 2026-10-08 unless noted)
- ChatGPT Plus limits: aiplanfinder.com/chatgpt-usage-limits and chatai.guide (both citing OpenAI's help center); third-party, unverified.
- Gemini limits, context window and usage meter: support.google.com/gemini/answer/16275805
- Grok plans and the weekly pool: freeacademy.ai/blog/grok-free-vs-supergrok-2026
- Quota reset behaviour of ChatGPT (reset time shown once a limit is hit) and Grok (early, unannounced resets): supplied by a tester on 2026-10-09, not re-verified here.
- DeepSeek V4 and data jurisdiction: deepseekai.guide/guides/deepseek-limitations
- Antigravity rules, workflows, planning mode and review policy: antigravity.google/docs/rules-workflows and antigravity.google/docs/artifact-review
- Judge biases and cross-family panels: memx.app/blog/llm-as-a-judge-biases-and-fixes ; arxiv.org/pdf/2606.03650
- Orchestration pitfalls (orchestrator context bloat, synthesis inventing consensus): glukhov.org/ai-systems/architecture/multi-agent-orchestration-patterns
- AI Studio as an unpaid service (use to improve products, human reviewers, "Do not submit sensitive, confidential, or personal information", what counts as paid): ai.google.dev/gemini-api/terms (effective 2026-03-23, updated 2026-04-28)
- OpenRouter free-model limits, prompt logging and locally stored chat rooms: openrouter.ai/docs/faq
- Gemini Notebook (NotebookLM) data use and feedback review: support.google.com/notebooklm/answer/16164461
- Suno credits per generation (10 for two songs), download caps and commercial rights: flexprice.io/pricing-index/suno (updated 2026-09-30) and mubert.com/blog/suno-download-caps (Aug 2026)
- ElevenLabs credits per character and plan rights: happyrobot.ai/hub/elevenlabs-pricing (Sep 2026)
- Perplexity free limits: aiplanfinder.com/plans/perplexity-free (verified Jul 2026)
- Higgsfield MCP tool descriptions (get_cost preflight, use_unlim, no blind resubmit after a timeout), read 2026-10-08.
- Claude usage limits and the usage page: ai-toolbox.co/claude-management-and-productivity/claude-usage-limits-2026 (Sep 2026) and fast.inference.net/guides/claude-usage (verified Aug 2026), both citing Anthropic's Help Center; checked 2026-10-09.
- Live test 2026-10-08: the same two-line question went to ChatGPT (Instant, temporary chat), Grok (Auto, private chat), DeepSeek (DeepThink and Search on) and Gemini (Flash). All four returned "Mount Logan | 5959 | Yukon" plus "ALL DONE", matching the Geological Survey of Canada's 1992 GPS figure of 5,959 m.
- Live test 2, 2026-10-08, same question: AI Studio (temporary chat, Gemini 3 Flash Preview), Perplexity (incognito), Kimi (K3 on www.kimi.ai) and Qwen returned it exactly; Gemini Notebook answered from a one-paragraph pasted source with a citation line and " ALL DONE"; OpenRouter's free models failed twice; Suno and ElevenLabs were dry runs; Higgsfield was a credits read and one cost preflight. File upload: ChatGPT read the uploaded test file and answered "BLUE-HERON-42"; AI Studio stopped at its media-terms dialog.

_multi-ai-delegation · designed by Mehrdadnsr_
