# OpenRouter (openrouter.ai/chat)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets and the loop: workers/common.md.

- Tiers: ":free" models cost nothing (Tier 2 for most users); paid models bill per token (Tier 3). Anything that may bill goes through the gate (SKILL.md 2.3).
- Data terms: assume ":free" model providers log prompts and may train on them; public, non-personal text only.
- Status: Relay-only (common.md 9) for real chunks until an answer has been read back. Inserting and sending worked, but both free models failed, so no answer element is known. When a plan includes OpenRouter, Claude may first drive one short trial prompt on a ":free" model; if it answers, find the answer element, use it for this run and report it for an issue or pull request (this file is replaced on every update).
- New room: https://openrouter.ai/chat . Rooms are stored in this browser only (not on the account); the room id is redacted in the tab list and blocked from JS reads, so log the room's title instead of a URL.
- Model: "Add Model (⌘J)", type ":free" or a model name, click the option; remove one with "Remove model" (x) on its chip. Several models in one room answer the same prompt side by side. Each model's settings include Provider, "Require Zero Data Retention", reasoning and the system prompt.
- Composer: `textarea[placeholder^="Ask anything"]`. Insert with snippet C (swap the selector).
- Send: JS click on `button[aria-label="Send message"]`.
- Last answer: not established, because both test answers failed; in the trial, look for it with get_page_text or a screenshot.
- Meter: openrouter.ai/settings/credits. With no credits, an "Insufficient credits" popover offers "Buy credits" (never) or "Continue with free models".
- Quirks: "Tools: 8 active" were on Auto (web search, web fetch, image generation, datetime, Fusion with 3 models, Advisor, Subagent, Shell): some call other models and could cost money on a paid run, so list them in the plan. Test: Gemma 4 31B (free) returned a provider error; the Free Models Router picked "North Mini Code (free)", which showed an empty reasoning block and no answer; Claude stopped after the two tries (common.md 8).

_multi-ai-delegation · designed by Mehrdadnsr_
