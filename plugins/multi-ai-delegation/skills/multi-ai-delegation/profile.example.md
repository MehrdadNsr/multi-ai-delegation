# Profile (example)

A template for your own profile. Fill in what applies and keep your copy in your own storage, never in the plugin folder: plugin files are replaced on every update. Claude reads the profile from the first of these that exists (SKILL.md 0.2): 1. memory, /topics/ai-delegation-profile.md; 2. with no memory tool (e.g. Claude Code), ~/.claude/ai-delegation-profile.md; 3. a profile you paste into the chat; 4. otherwise Claude asks up to 6 short questions and saves the answers with your OK. Blank fields take the defaults in the comments. Never put passwords, keys or card numbers here.

## Settings
<!-- On or off: a short welcome the first time the skill loads for you. Default: on. -->
- Welcome: on
<!-- The skill version you last saw. Claude fills it in and uses it for a one-line "what's new" after an update. -->
- Last version seen:
<!-- The Google account Claude may pick on a site's own "Sign in with Google" page when a site is logged out, only after your OK. Blank = the sign-in assist is off. -->
- Google sign-in account:

## Language and wording
<!-- The language of replies, plans and reports. Blank = the language you write in. Worker prompts stay in English. -->
- Output language:
<!-- Optional: script, terms or format wishes, e.g. "technical terms in English", "long reports as an HTML page". -->
- Style notes:
<!-- Optional: your wording for the one-line question Claude asks before offering to split a job. -->
- Ask-first question:
<!-- Optional: your own words for the commands; the English words always work. -->
- Command words: council: ; plan only: ; status: ; test: ; stop: ; go: ; about: ; resume:
<!-- Optional: the plan table's 8 column headers in your language, in order. Blank = Claude translates them. -->
- Plan table headers:
<!-- Optional: your wording for the lines under the plan table (personal data, storage, a long run, the closing question). -->
- Plan lines:

## Services and tiers
<!-- The AI sites you use and how you pay for each: this decides routing and the money rules (SKILL.md 2.2). A site listed nowhere counts as Tier 2 (free) unless it bills per use (Tier 3). No paid subscriptions is fine: Claude, its subagents and the free sites still work. -->
| Tier | Your services |
|---|---|
| 0 | Claude in the main chat and workspace code (always) |
| 0b | Claude subagents (they use your Claude plan's usage) |
| 1 | Subscriptions you pay for, e.g. a paid ChatGPT or Gemini plan |
| 2 | Free services you use, e.g. DeepSeek, Kimi, Qwen, Perplexity, OpenRouter ":free" models |
| 3 | Pay-per-use or credits, e.g. OpenRouter paid models, Suno, ElevenLabs, Higgsfield |

<!-- The most a paid tool you name yourself ("make this in Suno") may spend without asking; above it, Claude asks first. Blank = always ask. Example: 100 credits or USD 2. -->
- Own-pick threshold:
<!-- Optional notes per service: a preferred first route, a plan quirk, the domain that works for you (e.g. "Kimi: signed in on www.kimi.ai"). -->
- Notes:

## Projects (optional)
<!-- Projects Claude may route work for, with their rules (e.g. "music for my app's ads: Suno; consented voices only") and any brief-structure skill for coding briefs (modes/code.md). -->
- 

## Computer and browser
<!-- Your operating system: select-all is cmd+a on macOS and ctrl+a elsewhere. -->
- Computer:
<!-- Your browser, and any extension that injects text into chat sites (Claude ignores that text). -->
- Browser and extensions:
<!-- Optional: connector details that differ from the defaults, e.g. the exact ToolSearch select string for your Higgsfield connector. -->
- Connector notes:

## Localized UI labels
<!-- Only for sites whose interface is not in English: the labels Claude must match. How to find them: hover the button and read its tooltip, or run "test" (modes/test.md), which reads the send, stop and close labels of a non-English site and offers to add them here. Format: Site: English label = your label. -->
- Stop button:
- Popup close button:
- Gemini:
- Gemini Notebook:

_multi-ai-delegation · designed by Mehrdadnsr_
