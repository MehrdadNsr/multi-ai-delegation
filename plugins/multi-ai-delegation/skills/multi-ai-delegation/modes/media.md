# Media mode: music, voice, images, video

Tier 3 work: Suno (music), ElevenLabs (voice), Higgsfield (images and video, through its MCP tools, never the browser). Tier 1 alternatives: Gemini or ChatGPT for images when they can do the job; AI Studio's speech mode for stock-voice narration (untested). lifecycle.md applies; driving details: workers/suno.md, elevenlabs.md, higgsfield.md.

1. Images and video with no tool named: the plan offers both, Higgsfield with its get_cost quote and what it adds, and Gemini or ChatGPT (Tier 1) when they can do the job, and the user picks; if only Higgsfield can (a video model or control Tier 1 lacks), say so. It generates only after the user's yes. (The profile may name the user's preferred first route.)
2. Music and voice are Tier 3-only jobs: the plan names the site, says why nothing in Tier 0-2 can do the job, and gives the estimate (limits.md; Higgsfield: get_cost per job, plus one possible retry). It runs only after the user's explicit yes, whatever the amount. Offer AI Studio's speech mode for stock-voice narration.
3. User's own pick: when the user's message names a specific Tier 3 tool for a specific job ("make this shot in Higgsfield", "make a Suno track for this"), that is the user's choice: get the quote, state the cost in one line and go on without waiting, unless it is unusually high (over the profile's own-pick threshold; blank means always ask); then ask. The rest of the run still goes through the gate.
4. Credits: read the credit meter right before and right after, and report the actual spend next to the approved estimate or the one-line quote. Never spend unlimited or free-trial generations unless the user asks. Never top up, buy credits or downloads, switch on pay-as-you-go, upgrade or change plans; when credits run out, stop that site.
5. Failure: Higgsfield gets one retry, only once the first job has clearly failed (check its status first; never resubmit blind); if the retry fails, stop and report the error and the credits spent.
6. Likeness and voices: only the user's own face or voice, or those of people who consented; never clone or imitate a real person without that consent (SKILL.md 2.5).
7. Output: the user listens, watches and downloads the files; Claude never downloads. Downloads can count against a monthly cap (Suno), so the plan says how many results the user is likely to keep.
8. Generation prompts carry no run tag (templates.md 1): log the job ids, generation ids or song titles in the ledger instead.

_multi-ai-delegation · designed by Mehrdadnsr_
