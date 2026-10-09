# Known gaps (volatile)

Read before relying on a site or feature listed here. After every run, report what the run settled or found new, with dates, so the user can send it upstream as an issue or pull request (this file is replaced on every update).

- Stop controls were seen only on ChatGPT and Qwen ("Stop") and Kimi (the "stop" class). Not seen on Grok, DeepSeek, Gemini, AI Studio, Gemini Notebook, Perplexity or OpenRouter; the stable-length check carries the wait.
- Very long inputs are untested on every site: paste size, whether ChatGPT turns a long paste into an attachment, get_page_text's size cap, how AI Studio renders long answers (its turns sit in a virtual-scroll container), Kimi's and Qwen's real limits.
- OpenRouter: no last-answer selector yet, so it stays Relay-only (both free-model tries failed: a provider error, then an empty reasoning block); whether room settings (tools, zero data retention) persist.
- Suno and ElevenLabs: dry runs only (fields, buttons, meters); the real credit cost per generation, the model pickers, where results appear, completion and failure signals, Suno's public/private setting and lyrics insertion, and the download flow are untested. Suno's create page also showed speech fields (untested).
- Higgsfield: credit reads and one video cost preflight only; nothing generated; an image cost preflight was blocked by a session's permission check.
- AI Studio: uploads after the user accepts the media terms; whether removing Search grounding sticks; its speech mode for narration.
- Gemini Notebook: adding sources by file upload; the 5-hour limit notice; how citation markers land inside CSV rows; its English UI labels (only a localized UI was seen).
- Localized UIs: snippet D's STOP pattern and the Gemini and Gemini Notebook labels depend on the UI language; only English and one localized UI were seen.
- Perplexity: an account may show a Pro label on a free plan; the real Pro-search allowance is unknown.
- Grok plan and its exact quota cost per mode; DeepSeek's busy behaviour under load.
- Saved chats (the rule since 2026-10-09): chat URLs were seen on ChatGPT (/c/<id>), Grok (/c/<id> plus a query string), DeepSeek, Gemini, Gemini Notebook, Perplexity, Kimi and Qwen. Untested: AI Studio's normal-chat URL (both of its runs so far went out in a temporary chat, which keeps the base URL; the 2026-10-09 one because the check read only the heading) and whether it saves a normal chat at all, and resuming in a reopened chat on any site (for example a continue turn hours later).
- Claude subagents (Tier 0b): not yet run as workers; their real share of Claude usage per chunk, their speed (the 1-3 min per chunk in lifecycle.md 3.4 is a guess), and continuing one with SendMessage are untested. Reading the usage meter in Chrome worked on 2026-10-09.
- Run state: mirroring the run folder to a connected folder is untested (on 2026-10-09 a computer was linked with no folder connected), including whether device_commit_files overwrites the ledger without force; the memory run status and a resume from a new chat are untested; the outputs folder surviving a container restart was seen once.
- Pilot size (about 5%, at least 10) and the time rules of thumb are uncalibrated: log real pilots and durations in limits.md.
- New on 2026-10-09 and untested until a real run: canary items, the worker scorecard, recipes, the review chain, the challenge pass, the kill switch, the fresh-chat retry, plan-only mode. Tested that day: the extension check, the status command (all 13 workers signed in) and a two-worker council (ChatGPT for, Grok against).
- Copilot (added 2026-10-09): untested; no selectors yet; on one account copilot.microsoft.com redirected to an employer's sign-in, so it needs a personal Microsoft account signed in first.
- Careful-mode caps (2026-10-09) are guesses, not measured limits; no site publishes one.
- Meters not found on the chat pages in the status test: Grok's weekly % meter and Gemini's usage limits (Settings, Usage limits); their exact locations are unconfirmed.
- Public release (2026-10-09), untested until real use: the first-run setup, the profile in ~/.claude/ai-delegation-profile.md, state under ./ai-runs/, the what's-new line and the test command; nothing has been tested in Claude Code yet.
- Google sign-in assist (added 2026-10-09): untested until a real run, including each site's Google button, the account chooser, the "Continue as" confirmation and the return to the site.

_multi-ai-delegation · designed by Mehrdadnsr_
