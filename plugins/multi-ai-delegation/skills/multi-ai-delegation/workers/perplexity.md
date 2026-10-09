# Perplexity (www.perplexity.ai)

Verified 2026-10-08; UIs change, so if a selector fails fall back to `find` plus a 0.3-scale screenshot. Snippets, LAST and the loop: workers/common.md.

- New thread: https://www.perplexity.ai/ (saved in the user's history). Never incognito (anonymous threads, not saved to history, expire after 24 h): its button's aria-label starts "Use incognito" while off and reads "Exit incognito" while on. It persists across page loads, so check it before each new thread (common.md 3, step 4).
- Composer: `#ask-input` (contenteditable). Insert with snippet A (swap the selector), then read back in a separate call after 2 s; never insert twice. Clear leftovers with click, select-all, BackSpace (common.md 2).
- Send: JS click on `button[aria-label="Submit"]` (it replaces the voice-mode button once there is text). The URL becomes /search/<id>.
- Last answer: LAST in common.md 6. Related-question chips follow the answer; read only .prose.
- Mode: the "Model" button and the Search / Computer controls by the composer; left unchanged in the test. No Stop control seen.
- Meter: plan limits in limits.md; an account may show a Pro label while on a free plan, so read what it shows.

_multi-ai-delegation · designed by Mehrdadnsr_
