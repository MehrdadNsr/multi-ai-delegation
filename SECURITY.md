# Security policy

## Reporting

Please report security problems privately, not in a public issue: use **Report a vulnerability** on this repository's **Security** tab (GitHub private vulnerability reporting). Include the file and section, what could go wrong, and a way to reproduce it without anyone's personal data.

Useful reports include: page text or a worker's answer that makes Claude follow it (prompt injection) or skip the plan gate; a path that could send personal data somewhere the user did not approve; anything that could spend credits, accept terms or sign in without the user's OK.

## What the skill does and does not do

- It is a set of Markdown instructions for Claude. It fetches no remote instructions, runs no background code and collects no data; nothing is sent to the author.
- Data goes only to the sites in a plan the user approves, through the user's own browser session, and stays in those sites' histories under their terms.
- The profile and run state stay in the user's own storage (Claude's memory or local files).
