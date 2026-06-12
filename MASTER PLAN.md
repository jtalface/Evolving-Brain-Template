# Master Plan

The full architecture and phased build plan for the Evolving Brain.

## The problem this solves

Existing "AI memory" tools remember what an AI agent did across coding sessions. That's agent-session memory — useful, but not the goal here.

This is **personal second-brain memory**: a system that ingests raw life data from every app you already use, synthesizes it into a living wiki of you, lets Claude read it from any surface, and proactively surfaces patterns you'd otherwise miss.

## Architecture (one-line summary)

Markdown vault in private GitHub → `.inbox/` landing zone → scheduled processor → synthesized Live Logs + entity pages → MCP server exposes the vault to any Claude surface → Obsidian (local) and a Wikipedia-clone site (published) for visualization.

## Why markdown + git and not a database

- Obsidian works out of the box, including the graph view.
- Git gives free history, diffs, rollback, and version control.
- Any MCP or Claude surface can read markdown without a driver.
- Your data lives on disk, under your account, in a private repo. No vendor lock-in.
- Processing is stateless — any Claude instance with repo access can run the processor.

## Two memory layers, one store

1. **Life memory** (you write, the processor synthesizes): flows into `2 - Live Logs/ACTIONS_LOG.md` and entity pages.
2. **Assistant memory** (Claude writes): actions Claude took on your behalf. Flows into `2 - Live Logs/ASSISTANT_ACTIONS_LOG.md`.

Both are append-only markdown. Both readable by any Claude surface via the same MCP tools.

## Phases

### Phase 0 — Vault scaffold ✅
8-folder PARA structure + North Star + Operations + AGENTS.md. Push to private GitHub.

### Phase 1 — Capture contract + onboarding + ops
- `.inbox/` landing zone
- `Onboarding/` folder with question templates
- `9 - Operations/workflows/` — inbox processing, onboarding processing, wiki generation
- `Vault/` credentials store
- `.claude/commands/` slash commands

### Phase 2 — First onboarding run
- Fill out `Onboarding/01` and `02`
- Dump exports from existing tools into `.inbox/onboarding/`
- Run the onboarding processor
- Review and edit generated Identity and Aspirations files

### Phase 3 — First connector wired end-to-end
- Pick one source (recommendation: meeting notetaker)
- Wire it to drop files into `.inbox/meetings/`
- Run inbox processing manually to verify the path

### Phase 4 — Scheduled processing
- Move the manual processor run to a scheduled job
- GitHub Actions on a cron (free, private, simple)
- Cadence: every 3 hours

### Phase 5 — MCP server (Claude reads you from anywhere)
- A thin MCP server exposing: `search_vault`, `read_entity`, `append_to_inbox`, `get_context`, `get_north_star`, `list_projects`, `log_assistant_action`
- Alternative: adopt gbrain (garrytan/gbrain) as the retrieval layer if you already have Supabase

### Phase 6 — Visualization layer
- **Obsidian** (local, private): open the vault folder, graph view and backlinks work for free
- **Wikipedia-clone site** (optional, published): static site from markdown via Quartz 4 or Astro

### Phase 7 — Proactive reviews
- Scheduled weekly review committed to `8 - North Star/reviews/`
- If a North Star metric drifts, open a GitHub Issue
- If a review surfaces a potential identity shift, flag it — never auto-edit Identity

## What this is NOT

- Not a database. Markdown only.
- Not a real-time sync system. Cron every few hours is enough.
- Not a replacement for your capture tools. Synthesis + retrieval on top.
- Not coupled to Claude Code specifically. Works with any Claude surface.
- Not a public repo. Fork this template and go private immediately.
