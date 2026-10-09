# DeepSeek (chat.deepseek.com)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- Free service under Chinese jurisdiction: public, non-personal text only, unless the user names DeepSeek for that material (SKILL.md 2.5).
- New chat: https://chat.deepseek.com/ . No temporary mode; chats are saved and auto-titled (/a/chat/s/<id>). While loading it briefly redirects to /sign_in: wait 3 s and check again.
- Composer: `textarea` (placeholder "Message DeepSeek"). Insert with snippet C.
- Send: left_click the textarea (find gives the ref), then key Return. Clicking the arrow button's ref did not send.
- Last answer: LAST in common.md 6, the last `.ds-markdown` inside the last `.ds-message`; the earlier ones are the DeepThink trace, which is never read. Read with JS slices: get_page_text returns the whole body including the sidebar's chat titles.
- Toggles: DeepThink and Search (both were on in the test account); restore them at the end if you change them. With DeepThink on, wait until the header reads "Thought for N seconds" (common.md 4).
- Meter: no published web cap; "server busy" under load; DeepThink is slower.

_multi-ai-delegation · designed by Mehrdadnsr_
