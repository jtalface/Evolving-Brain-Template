# Evolving Brain — Template

A template for building your own AI-native second brain / Life OS. Fork it, make your fork private, run the setup, and let it grow.

> This is the **public template**. Do not fill in your actual identity, goals, or journal entries here. Fork it first, go private, then onboard.

## One-command setup (after you fork and clone)

```bash
git clone https://github.com/<your-username>/<your-fork>.git evolving-brain
cd evolving-brain
bash scripts/setup.sh
```

Then, inside Claude Code, run `/brain-onboard` (or `/brain-discover` to scan your machine for markdown sources first).

## What this is

A markdown vault designed to be the source of truth for a personal AI assistant that actually remembers you. Capture tools (Heptabase, Apple Notes, voice memos, meeting notetakers, Claude on your phone) drop raw content into an `.inbox/`. A processor runs on a schedule, synthesizes it into living logs and entity pages, and commits back. Any Claude surface can read the vault via a thin MCP server.

> You are a writer compiling, not a filing clerk. The question is never "where do I put this fact?" It is: "what does this mean, and how does it connect to what you already know?"

## The three-folder core

- `0 - Identity` — **who you are** (core, stable, changes rarely)
- `1 - Aspirations` — **who you are becoming** (goals, habits, projects, open problems)
- `2 - Live Logs` — **the raw signal of your life** (actions, decisions, emotions, learning, reflections)

## How to use this template

1. **Fork + go private** — never fill in personal data on a public fork
2. **Run setup** — `bash scripts/setup.sh`
3. **Run onboarding** — `/brain-onboard` inside Claude Code
4. **Wire a connector** — pick one source (recommend: meeting notetaker)
5. **Schedule the processor** — GitHub Actions on a cron is the simplest path

## Daily commands

- `/brain-capture "thought"` — drop a thought into `.inbox/manual/`
- `/brain-brief` — morning briefing
- `/brain-status` — read-only status report
- `/brain-review weekly` — weekly review
- `/brain-quick-wiki` — build a Wikipedia-style static site from your vault
- `/brain-sync` — check upstream sources for changes

## Folder map

| Folder | Purpose |
|---|---|
| `0 - Identity` | SOUL, decision-making principles, intellectual blueprint |
| `1 - Aspirations` | Goals, habits, active projects |
| `2 - Live Logs` | Actions, decisions, emotions, learning, reflections |
| `3 - Daily Journal` | Raw daily entries |
| `4 - Meetings` | Meeting notes |
| `5 - Projects` | PARA projects (defined outcome, end date) |
| `6 - Areas` | PARA areas (ongoing responsibilities) |
| `7 - Resources` | PARA resources (reference material) |
| `8 - North Star` | Leverage metrics you're optimizing for |
| `9 - Operations` | Workflows, connectors, skills, schedule, run history |
| `People` | One page per person who matters |
| `.inbox` | Landing zone for raw captures |
| `Vault` | Credentials store (`.env` gitignored) |
| `scripts` | Setup and install helpers |

## License

MIT. See `LICENSE`.
