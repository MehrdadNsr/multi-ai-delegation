# Grok (grok.com)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- New chat: https://grok.com/ (a normal chat, saved in the sidebar). Never "Switch to Private Chat" (top right, link to /c#private). A normal chat gets /c/<id> plus a query string to drop (seen 2026-10-09); the earlier private test chat kept the URL at "/". Confirm sending by the user message appearing or the URL changing.
- Composer: `div.tiptap.ProseMirror[contenteditable="true"]` (aria-label "Ask Grok anything"). Insert with snippet A.
- Send: JS click on `form button[aria-label="Submit"]`.
- Last answer: LAST in common.md 6. It starts with a "Worked for N s" line, Grok's end-of-thinking signal: save the answer after it. In a background tab the answer may not render until the tab is painted (2026-10-09): take small screenshots between polls (common.md 2). Long reads: get_page_text (main column only). Suggestion chips under the answer can echo the run tag; never click them.
- Mode: "Model select" button (Auto / Fast / Expert). No Stop control was seen yet (the answer took under 2 s); rely on the stable-length check.
- Meter: paid plans show usage as a weekly % meter (not visible on the chat page on 2026-10-09; location unconfirmed). They share one weekly pool, which can reset early and unannounced: take the reset time from the meter, never from a fixed weekly cycle. Expert drains the pool fast (limits.md).
- Phrasing: gives real pushback when asked to "argue against this", but filter it; it tends to mirror the framing it is given.

_multi-ai-delegation · designed by Mehrdadnsr_
