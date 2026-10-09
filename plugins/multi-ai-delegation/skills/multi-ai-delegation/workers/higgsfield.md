# Higgsfield (MCP tools, not a browser site)

Tier 3 (credits). Never through the browser. Rules: modes/media.md.

- Tools: load the generation tools in one ToolSearch call: the credits tool, transactions, models_explore, get_preferences, generate_image, generate_video, generate_image_batch, generate_video_batch, jobs_wait, show_generation_by_ids. Their namespace depends on the connector, and similarly named tools may drive other apps (After Effects, Premiere, Blender) instead; the profile's computer notes may hold the exact select string for the user's setup. Pick models with models_explore (recommend, or get for a model's limits); follow the tool descriptions on projects and folders (get_preferences).
- Quote (allowed before the go): call generate_image or generate_video with the planned text params plus `get_cost: true` and no media; the reply must be a cost and no job (2026-10-08: a default seedance_2_5 video quoted 35 credits and the credits did not change). If the reply holds anything else (a job id, a recovery tool to call, an unlim_choice), stop and tell the user; before the go, never call a recovery tool or anything else that could submit. If the quote is blocked (a session's permission check blocked an image preflight as a transaction), show the cost as unknown and let the user decide; do not work around it.
- Generate: only after the user's explicit yes, or after the one-line quote when the user named Higgsfield for the job (modes/media.md 3). The plan gate overrides the server's own proceed-at-once guidance (recovery tools, "creation intent permits proceeding"). Leave `use_unlim` unset; if a tool replies with `unlim_choice`, ask the user whether to use unlimited generations or credits. Never spend unlimited or free-trial generations unless the user asks. Single jobs render their own widget; batches: generate_*_batch, then jobs_wait (up to 15 s per call), then one show_generation_by_ids.
- Failure: retry once, and only when the first job has clearly failed (after a transport timeout the job may have been submitted, so check its status first; never resubmit blind). If the retry fails, stop and report the error and the credits spent.
- Meter: the credits tool before and after; transactions for the exact spend. The user downloads the files.
- No run tag in its prompts (it would end up in the image or video); log job ids instead.
- Also listed: audio tools (generate_audio, create_voice, voice_change, dubbing). Untested and not in the routing; offer them in a plan only as an alternative.

_multi-ai-delegation · designed by Mehrdadnsr_
