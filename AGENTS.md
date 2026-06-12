# AGENTS

## Self-updating

- When you learn something new about the user's projects, identity, or aspirations mid-conversation, suggest updates to relevant vault files.
- Don't update on every conversation — only when something genuinely lasting emerges.
- Always ask before making changes to files.

## Reading order
When picking up context at the start of a session, read in this order:
1. `0 - Identity/SOUL.md`
2. `0 - Identity/DECISION MAKING PRINCIPLES.md`
3. `8 - North Star/NORTH STAR.md`
4. `1 - Aspirations/GOALS.md`
5. `1 - Aspirations/ACTIVE PROJECTS.md`
6. Any live log relevant to the current task.

## North Star check
When the user proposes a new project, automation, or commitment, sanity-check it against the North Star metrics in `8 - North Star/NORTH STAR.md`. Flag tradeoffs explicitly.

## Writing rules
- Never overwrite `0 - Identity/` files without explicit confirmation.
- Append to live logs with dated entries; do not rewrite history.
- When the user asks to "log" something, infer the right log from the content (action / decision / emotion / learning / reflection).

## Logging your own actions
When you complete a meaningful action — drafted a doc, sent a message, created a file, ran a deploy — append an entry to `2 - Live Logs/ASSISTANT_ACTIONS_LOG.md`. Include outcome and undo steps. Log things the user would want to know happened. Do not log reads, searches, or trivial tool calls.

## Capture pipeline
When the user asks you to "capture" or "remember" something mid-conversation, write it to `.inbox/manual/YYYY-MM-DD-HHMMSS-<slug>.md` with proper frontmatter (see `.inbox/README.md`). The next processor run will integrate it.

## Operations layer
`9 - Operations/` is the runtime layer. Before running a workflow, read `9 - Operations/workflows/<workflow name>.md`. After finishing: update `last_run`, append a row to `9 - Operations/runs/YYYY-MM.md`, and update the workflow registry if needed.

## Credentials
Never hardcode secrets. All secrets live in `Vault/.env` (gitignored). The committed `Vault/key-inventory.md` catalogs what keys exist. If a workflow needs a new key, add it to `.env`, `.env.example`, and `key-inventory.md` in the same commit.

## Slash commands
- `/brain-onboard` — progressive onboarding walkthrough
- `/brain-capture <thought>` — drop a thought into `.inbox/manual/`
- `/brain-status` — read-only status report
- `/brain-brief` — morning briefing
- `/brain-discover` — scan the machine for markdown sources
- `/brain-quick-wiki` — build the Wikipedia-style static site
- `/brain-review [weekly|monthly|quarterly]` — review workflow
- `/brain-sync [source]` — check upstream sources for changes
- `/brain-tidy` — clean up stray files (invoke explicitly only)

## Entity pages (compiled truth + timeline)
All `People/`, `5 - Projects/`, `6 - Areas/` pages use the compiled-truth + append-only timeline pattern. Top = current best understanding (rewritable). Bottom = append-only evidence trail (never rewritten). Contradictions get a ⚠️ callout — never silently resolved.

## Citations are non-negotiable
Every fact written into the vault must be traceable to its source. Log entries end with `→ [[source]]`. When in doubt, over-cite.

## Persistent entity IDs
Every entity page has an `id` field in frontmatter. Never change the `id` on rename — update `aliases` instead.
