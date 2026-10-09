# Test mode: does each site still work?

"test" (or the user's word for it), optionally naming sites: one tiny known-answer prompt per chosen worker, to confirm the site still works after UI changes. lifecycle.md 1-4 apply (extension check, status, plan, go); no pilot, QC or merge.

1. Choose: the sites the user names; otherwise every chat site in the user's profile, or, with none listed, the sites the status check finds signed in. Credit sites (Suno, ElevenLabs, Higgsfield, OpenRouter paid models) get a dry check only: open the page, find the input and the generate control, read the meter; never generate.
2. Plan: one row per site, 1 prompt each, "minimal" in the quota column, about 1-2 min per site with the sites in parallel; then wait for the go (SKILL.md 2.3). The canary holds no personal data.
3. Send each site the canary (templates.md 11) in a new saved chat with the normal loop (workers/common.md 3), in the mode the site is in; change no toggles. Gemini Notebook answers only from its sources, so first add a one-line pasted source stating both facts (workers/notebook.md).
4. Pass: the answer's first line reads "Au | 366" (case, extra spaces and a final period ignored) and an ALL DONE line follows. Note each step's outcome: open, sign-in, insert, send, wait (done detection), read (LAST), answer.
5. Report in a small table: Site | Result (OK, or the step that failed) | Error text | Time. The test chats stay in each site's history with their run tag; Claude deletes none.
6. A site whose UI is not in English: read the aria-labels of its send, stop and popup-close buttons and offer to add them to the profile's UI labels.
7. A failure: draft an issue for the repository's "Site broke" template (.github/ISSUE_TEMPLATE/site-broke.md; the repository link is in SKILL.md's header): site, date, UI language, mode, the step that failed, the exact error text, the skill version, and what worked if Claude adapted a selector (workers/common.md 8). No personal data in it: no emails, account names, chat URLs or ids, chat titles, credit amounts or screenshots. Show it in one code block for the user to post; never post it (publishing is the user's call).

_multi-ai-delegation · designed by Mehrdadnsr_
