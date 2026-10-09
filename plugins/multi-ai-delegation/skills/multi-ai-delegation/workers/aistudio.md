# Google AI Studio (aistudio.google.com)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- Data terms: without a Cloud project with billing, AI Studio runs under Google's unpaid-service terms (a Gemini app subscription doesn't change that): prompts and answers may be used to improve Google's products and read by human reviewers, and Google says not to submit sensitive, confidential or personal information. No personal data here (SKILL.md 2.5).
- New chat: https://aistudio.google.com/prompts/new_chat . Use a normal chat, never "Temporary chat" (in "View more actions", the three-dot button in the header; while on, the heading reads "Temporary chat"). The test used a temporary chat, which kept the new_chat URL, so whether and where a normal chat is saved is untested: log the URL the tab shows after Run; if it stays at new_chat, treat the chat as unsaved (no resume there) and say so in the report (gaps.md). The same menu has Compare mode and Raw Mode.
- Composer: `textarea[aria-label="Enter a prompt"]`. Insert with snippet C (swap the selector).
- Send: JS click on the button whose aria-label or innerText starts with "Run" (its innerText also carries the shortcut icons).
- Last answer: LAST in common.md 6. The model's "Thoughts" come as a separate turn before it; never expand them.
- Mode: Run settings shows the model (Gemini 3 Flash Preview on 2026-10-08) and the thinking level. A "Grounding with Google Search" chip was on; for input-only extraction remove it with its remove control and check it stays off.
- Meter: the running token count by the composer; the free tier's rate limits are not shown in the UI.
- Quirks: the answer typed out slowly in a hidden tab (common.md 2). A huge file: paste its text, or upload it once the user has accepted the one-time media terms (at most 10 MB per call, common.md 2); until then the user attaches it. The first upload's "Start creating with media in Google AI Studio" terms dialog gets Cancel: accepting terms is the user's call.
- Speech mode: may do stock-voice narration (untested; modes/media.md).

_multi-ai-delegation · designed by Mehrdadnsr_
