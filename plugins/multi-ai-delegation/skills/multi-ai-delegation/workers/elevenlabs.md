# ElevenLabs (elevenlabs.io)

Tier 3 (credits). Dry run only on 2026-10-08: nothing generated. Snippets and the loop: workers/common.md; rules: modes/media.md.

- Text to speech: https://elevenlabs.io/app/speech-synthesis/text-to-speech . An "Eleven v4" promo dialog appeared: "Continue without switching" (don't change the model unasked).
- Composer: `textarea[placeholder^="Start typing here"]`. The value setter did not register; snippet F did. Clear with `ta.select(); document.execCommand('delete')`.
- Generate: the "Generate speech" button (no label in the DOM; get it with find), only after the user's explicit yes, or after the one-line quote when the user named ElevenLabs for the job (modes/media.md 3).
- Meter: https://elevenlabs.io/app/subscription (it redirected to /app/subscription/creative on 2026-10-09), "Credits used", shown as "N credits / M credits". The Free plan has no commercial license (limits.md), so commercial use such as ads needs a paid plan: the user's decision. Never buy or upgrade.
- Voices: only the user's own voice or voices whose owners consented. Output: the user downloads the files.
- No run tag in its text (it would be spoken); log generation ids instead.
- Not established yet: the model and voice pickers, where the audio appears, and how completion and failure show.

_multi-ai-delegation · designed by Mehrdadnsr_
