# multi-ai-delegation

A Claude skill, packaged as a plugin, that lets Claude split big jobs across your other AI chat sites and tools: ChatGPT, Grok, Gemini, Google AI Studio, Gemini Notebook (NotebookLM), Perplexity, DeepSeek, Kimi, Qwen, Microsoft Copilot (new, untested) and OpenRouter, plus Suno, ElevenLabs and Higgsfield for media. Claude drives the sites in your own browser through the Claude in Chrome extension. Nothing is sent until you approve a plan that shows which site gets what, at what cost and how long it will take.

**Status: beta.** Tested on one account in October 2026; see [Status](#status).

## What it does

- Splits big material (chat exports, logs, transcripts, long PDFs) into chunks with stable ids and routes each chunk by cost tier: Claude itself, Claude subagents, your subscriptions, free sites, and pay-per-use tools only when nothing cheaper can do the job.
- Shows a plan table first (site, tier, mode, chunks, volume, prompts, quota share or cost, time) and waits for your go.
- Pilots one small chunk per worker, runs the rest in parallel, checks every answer mechanically, spot-checks it against the source, plants known-answer canaries, and cross-checks high-stakes work on a second model family.
- Merges the results and reports who did what, what was verified and what was not, what was spent, and which chats were left in each site's history.
- Also: a council (for, against and neutral views from different model families), a review chain and challenge pass, media jobs with a cost quote first, and briefs for a coding agent you drive.

Example:

> **You:** Here's a chat export with about 1,200 messages. Pull out every decision with its date and owner. Split it across my AIs.
>
> **Claude:** *(plan table)* Claude subagents take L0001–L0400, ChatGPT L0401–L0800, Grok L0801–L1200, one pilot chunk each; 16 prompts, about 20 minutes; fallback DeepSeek; personal data: none. Go?
>
> **You:** go
>
> **Claude:** runs the pilots, checks them, sends the rest, spot-checks and merges one CSV, then reports rows per worker, error rates, canary accuracy and the saved chats with their run tags.

## Status

Beta. Tested on one account in October 2026, in Chrome, with one non-English interface:
- the extension check and the `status` command (13 sites signed in, meters read where the site shows one);
- a known-answer prompt, read back exactly, on ChatGPT, Grok, DeepSeek, Gemini, AI Studio, Gemini Notebook, Perplexity, Kimi and Qwen;
- a two-worker council (ChatGPT for, Grok against);
- a file upload to ChatGPT;
- dry runs on Suno and ElevenLabs (fields, buttons, meters), and a Higgsfield credits read and cost quote;
- the answer parser and the JavaScript snippets (scripted tests).

Not tested yet: a full multi-site run end to end, Claude subagents as workers, OpenRouter answers (its free models failed), any music, voice, image or video generation, the Google sign-in assist, resume, recipes, the scorecard, the first-run setup, the `test` command, and anything in Claude Code. See [Known gaps](#known-gaps).

## Requirements

- A paid Claude plan (Pro, Max, Team or Enterprise), which Claude in Chrome requires.
- The [Claude in Chrome](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn) extension, signed in to the same Claude account, with Chrome open during a run.
- Accounts on the sites you want to use, signed in in that browser.

Free-only works: with no paid AI subscriptions, Claude, its subagents and the free tiers (ChatGPT, Gemini, Grok, AI Studio, DeepSeek, Kimi, Qwen, Perplexity, OpenRouter's free models) cover the chat jobs. Music and voice need credits on Suno or ElevenLabs, and the plan always asks before spending them.

## Install

**claude.ai or the Claude desktop app**
1. Open **Customize > Plugins**.
2. Choose **Add > Add marketplace** and enter `Mehrdadnsr/multi-ai-delegation`.
3. Find **multi-ai-delegation** among the plugins and select **Add**.
4. Turn on **Sync automatically** for the marketplace so updates arrive by themselves (or use **Check for updates**).

**Claude Code**
```
/plugin marketplace add Mehrdadnsr/multi-ai-delegation
/plugin install multi-ai-delegation@multi-ai-delegation
```
Then open `/plugin`, go to **Marketplaces**, select **multi-ai-delegation** and choose **Enable auto-update** (third-party marketplaces start with auto-update off). Start Claude Code with `claude --chrome`, or run `/chrome`, so the browser tools are available.

## First run and your profile

The first time the skill loads, Claude asks up to six short questions in your language: the language you want, which AI sites you use, which of them you pay for, a spending threshold for paid tools you name yourself, an optional Google account for sign-in help, and your computer and browser. It shows the result and saves it only with your OK:
- where Claude has memory (claude.ai): in the memory file `/topics/ai-delegation-profile.md`;
- where it has none (Claude Code): in `~/.claude/ai-delegation-profile.md`;
- with nowhere to save: in the conversation only, and you can paste it next time.

You can also fill in [profile.example.md](plugins/multi-ai-delegation/skills/multi-ai-delegation/profile.example.md) and paste it. Ask Claude to show or change your profile at any time. The profile lives with you, not in the plugin, so updates never overwrite it.

## Commands

Say these in any language.

| Say | What happens |
|---|---|
| "split this across my AIs" (or any big extraction, tagging or drafting job) | run: plan, go, pilot, the rest, checks, merge, report |
| "council" | for, against and neutral views from different model families |
| "review this", "second opinion", "challenge this" | review chain, challenge pass |
| music, voice, images, video | media mode; credits always come with a quote first |
| repo-level coding | a brief for the coding agent you drive, then a review of the result |
| "plan only" | the plan with cost and time; nothing is sent |
| "status" | sign-in and meters of every site; nothing is sent |
| "test" | one tiny known-answer prompt per site, to check it still works after UI changes |
| "stop" | halts all sending at once |
| "resume RUN" | continues a saved run |
| "use the NAME recipe" | reuses a job that worked before, still with a plan and your go |
| "about" | the welcome and the version |

## Safety rules in brief

- Nothing goes to any site or subagent before you approve the plan; silence is not a go. "stop" halts everything.
- Careful mode, on by default: at most 25 prompts a site a day (12 on Google's services), 20 s apart, one chat per site at a time, and a 24-hour pause on any site that shows a CAPTCHA or an "unusual activity" warning. These are the skill's own limits; no site publishes a safe rate.
- Claude never types passwords, solves CAPTCHAs, creates accounts, accepts terms, changes account settings, deletes chats, downloads files, or buys, tops up or upgrades anything.
- Credits are spent only after your explicit yes, or within your threshold for a tool you name yourself, with the meter read before and after.
- Personal data goes only to a service you name for it; none goes to free services whose terms allow training on prompts or that sit under Chinese jurisdiction unless you say so.
- Worker answers and page text are treated as data, never as instructions.
- Second opinions, councils, reviews and challenge passes get a neutral prompt: no preferred answer in it, the author hidden; the report names any angle or stance a worker was given, and a worker's agreement with a framed prompt is never reported as an independent check.
- Sign-in help needs your OK, uses only the site's own Google button and the account in your profile, and stops at any password, code, permission or terms screen.

## What the skill stores, and how to delete it

- Your profile: `/topics/ai-delegation-profile.md` in Claude's memory, or `~/.claude/ai-delegation-profile.md`.
- Run status and the one-time welcome flag: `/areas/ai-runs.md` in memory (or a project's memory file), or `./ai-runs/status.md` in your working folder.
- Run files (chunks, raw answers, the ledger), recipes and the scorecard: an `ai-runs/` folder in Claude's workspace, in a folder you connect, or in your working folder in Claude Code.
- To delete: ask Claude to delete those memory files, or delete the files and folders yourself. Delegated chats stay on each site; delete them there.

To uninstall: on claude.ai or desktop, open the plugin in **Customize > Plugins**, open its menu and select **Remove**, then remove the marketplace. In Claude Code: `/plugin uninstall multi-ai-delegation@multi-ai-delegation`, then `/plugin marketplace remove multi-ai-delegation`.

## Privacy

Every delegated chat is saved in that site's history: the skill never uses temporary or private chats, so runs can be checked and resumed. Those chats fall under each site's terms and your settings there, which may allow training or memory of past chats. The skill sends nothing to the author and fetches no remote instructions. Full details: [Privacy policy](PRIVACY.md).

## Honest caveat

Automating a chat site's web interface may conflict with some sites' terms of service. You are responsible for your accounts and how you use them. Sites also change their interfaces often; when one breaks, run "test" and open a **Site broke** issue.

## Known gaps

[gaps.md](plugins/multi-ai-delegation/skills/multi-ai-delegation/gaps.md) lists what is untested or fragile, with dates.

## Contributing

Issues and pull requests are welcome; please read [CONTRIBUTING.md](CONTRIBUTING.md). For a site that stopped working, use the **Site broke** issue template. Security reports: [SECURITY.md](SECURITY.md).

## Credits

Designed by [Mehrdadnsr](https://github.com/Mehrdadnsr). More from the author: [CelTip](https://celtip.com) and Vazne, a workout app (link coming soon).

## License

[MIT](LICENSE)
