# ChatGPT (chatgpt.com)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- New chat: https://chatgpt.com/ (a normal chat, saved in history as /c/<id>, seen 2026-10-09; a temporary chat adds ?temporary-chat=true). Never use temporary chats (https://chatgpt.com/?temporary-chat=true) for delegation: the chats must be saved. A "Save chat" popover may appear; ignore it. A "Meet ChatGPT Work" dialog may appear; close it via find, then click the close ref.
- Composer: `div.ProseMirror[contenteditable="true"]` (aria-label "Ask ChatGPT"). Insert with snippet A.
- Send: click the form button with aria-label "Send". While generating it turns into "Stop".
- Last answer: LAST in common.md 6. Long reads: get_page_text (returns only the main column, no sidebar); take the text after the last "ChatGPT said:", without any reasoning summary (common.md 4).
- Mode: the "Select ChatGPT model" button shows the current mode (Instant / Thinking).
- File upload: find the hidden input "Attach files", then file_upload with a working-directory path; the file chip shows in the composer form (common.md 2).
- Meter: nothing shows until a limit warning. Once a limit is hit, ChatGPT says when that allowance resets; there is no fixed published cycle for paid plans, so take the reset time from that message (limits.md figures are unverified third-party information).
- Phrasing: follows explicit formats closely.

_multi-ai-delegation · designed by Mehrdadnsr_
