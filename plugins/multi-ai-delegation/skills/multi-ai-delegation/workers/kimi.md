# Kimi (www.kimi.ai)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- Free service under Chinese jurisdiction: public text only, unless the user names Kimi for that material (SKILL.md 2.5).
- New chat: https://www.kimi.ai/ . On one account kimi.com showed "Log in" and sending hit a login wall while the session was signed in on www.kimi.ai, so if one domain is logged out, try the other once. Chats are saved and auto-titled (/chat/<id>, with a query string to drop); no temporary mode checked.
- Composer: `div.chat-input-editor` (contenteditable). Insert with snippet A (swap the selector); the text lands after a moment, so read back after 2 s.
- Send: `.send-button-container` carries the class "disabled" while empty; dispatch a click on its inner svg: `(() => { const s = document.querySelector('.send-button-container'); if (!s || /disabled/.test(s.className)) return 'NOT_READY'; (s.querySelector('svg, button, div') || s).dispatchEvent(new MouseEvent('click', {bubbles: true})); return 'clicked'; })()`. While generating, its classes read "send-button-container disabled stop".
- Last answer: LAST in common.md 6, the last markdown block inside the last assistant item; the earlier ones are the "Thinking complete" trace, which is never read.
- Mode: the model label by the composer read "K3" ("K3" and "High" on 2026-10-09); left unchanged.
- Busy: under load a Tips dialog says too many people are chatting with Kimi and the prompt is dropped (twice on 2026-10-09). Click "Got it", never Upgrade; then the busy row in common.md 8.
- Meter: no published web cap found; it answered the first test within seconds.

_multi-ai-delegation · designed by Mehrdadnsr_
