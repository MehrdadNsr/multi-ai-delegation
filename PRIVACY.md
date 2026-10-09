# Privacy policy

Last updated: 2026-10-09

multi-ai-delegation is a set of Markdown instructions (a Claude skill, packaged as a plugin). It has no server, collects no data, and sends nothing to its author. This page describes what happens to data when you use it.

## What the plugin stores, and where

All of it stays in your own storage, never with the author:

- **Your profile** (output language, which AI sites you use and pay for, a spending threshold, an optional Google account email for sign-in help, computer and browser notes): saved only with your OK, in Claude's memory (`/topics/ai-delegation-profile.md`) or, where Claude has no memory, in `~/.claude/ai-delegation-profile.md` on your computer.
- **Run status and the one-time welcome flag**: in Claude's memory (`/areas/ai-runs.md`) or `./ai-runs/status.md` in your working folder. Run status holds ids, counts, chat links and file paths, not the content of your material.
- **Run files** (chunks, raw answers, a ledger): in an `ai-runs/` folder in Claude's workspace, a folder you connect, or your working folder.

Passwords, API keys and card numbers are never stored.

## What is sent, and to whom

- Only after you approve a plan, Claude sends the planned prompts and chunks to the AI sites named in that plan (for example ChatGPT, Grok, Gemini, DeepSeek, Kimi, Qwen, Perplexity, OpenRouter, Suno, ElevenLabs, Higgsfield), through your own browser session (Claude in Chrome) or a connector you added.
- Those chats are saved in each site's history and are handled under that site's own terms and privacy policy, and your settings there (which may allow training or memory). The plugin never uses temporary or private chats, so runs can be checked and resumed.
- Personal data goes only to a service you name for it in the conversation. By default none goes to free services whose terms allow training on prompts, or to services under Chinese jurisdiction.
- The plugin fetches no remote instructions and has no analytics or telemetry.

## Your choices

- View or change your profile at any time by asking Claude.
- Delete the memory files or local files listed above, or ask Claude to delete them.
- Delete delegated chats on each site.
- Uninstall the plugin (see the README).

## Contact

Open an issue at https://github.com/MehrdadNsr/multi-ai-delegation/issues, or for anything sensitive use private vulnerability reporting on the repository's Security tab.
