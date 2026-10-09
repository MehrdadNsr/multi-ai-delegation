# Gemini (gemini.google.com/app)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md. Labels follow the account's UI language; the profile's UI labels hold the user's localized ones.

- New chat: https://gemini.google.com/app . Chats are saved to Recent (/app/<id>).
- Composer: `div.ql-editor[contenteditable="true"]` (Quill). Insert with snippet B; the paste event of snippet A does nothing here.
- Send: JS click on the button whose aria-label is exactly "Send message" (in a localized UI, the localized label); other buttons contain the same word, so match the full label.
- Last answer: LAST in common.md 6. In a background tab it can stay empty until the tab is painted: take a 0.3-scale screenshot, then read again. get_page_text includes the sidebar, so read with JS slices.
- Mode: the mode-picker button says which mode is current (Flash / Thinking / Pro).
- Meter: Settings, Usage limits. Officially it refreshes every 5 hours up to a weekly cap (limits.md); take the reset time from the meter.
- Phrasing: tends to be verbose, so cap the length and ask for primary sources.

_multi-ai-delegation · designed by Mehrdadnsr_
