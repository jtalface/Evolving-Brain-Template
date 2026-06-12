# .inbox — Landing Zone

> Raw captures land here. The processor synthesizes them into the vault.

## Contract

Every file in `.inbox/` must have this frontmatter:

```yaml
---
source: manual | meeting | apple-notes | heptabase | voice | ...
captured_at: YYYY-MM-DDTHH:MM:SSZ
processed: false
---
```

## Subfolders

- `.inbox/manual/` — things you dropped in mid-conversation with Claude
- `.inbox/meetings/` — raw meeting transcripts from your notetaker
- `.inbox/onboarding/` — bulk exports from existing tools (one-time)
- `.inbox/processed/` — files the processor has already integrated (do not edit)

## What happens to files here

The inbox processor (`9 - Operations/workflows/inbox processing.md`) runs on a schedule, reads each unprocessed file, synthesizes key content into Live Logs and entity pages, sets `processed: true`, and moves the file to `.inbox/processed/`.
