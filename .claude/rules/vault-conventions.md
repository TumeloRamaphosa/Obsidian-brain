# Vault Conventions

## File Naming
- Use **Title Case** for all note names (e.g., `StudEx Meat.md`, `Business Plan Draft.md`)
- Daily logs use ISO dates: `YYYY-MM-DD.md`
- Weekly summaries: `YYYY-WXX-summary.md`

## Frontmatter
Every note MUST have frontmatter with at minimum:
```yaml
---
title: Note Title
tags: [relevant, tags]
created: YYYY-MM-DD
modified: YYYY-MM-DD
---
```

Business notes also include:
```yaml
type: business-profile | project | meeting | idea | research
status: active | planned | completed | archived
parent: "[[Parent Note]]"
```

Chat-extracted notes also include:
```yaml
source: chatgpt | gemini | claude | perplexity | manus | minimax | qwen | ollama
chat_date: YYYY-MM-DD
```

## Linking
- ALWAYS use [[wikilinks]] to connect related notes
- Business notes MUST link to their parent entity
- Every note should link to at least one other note (no orphans)
- Use [[Note Name|Display Text]] when the display text should differ

## Tags
Core tags:
- #studex — Core StudEx content
- #business — Business-related
- #action-item — Actionable task
- #idea — Unvalidated idea
- #research — Research content
- #decision — Decision record
- #meeting — Meeting notes
- #chat-extract — Extracted from AI conversation

## Folder Placement
- Business profiles → Notes/Businesses/<entity>/
- Projects → Notes/Projects/
- People → Notes/People/
- Knowledge → Notes/Topics/
- Ideas → Notes/Ideas/
- Meetings → Notes/Meetings/
- Daily logs → Daily/
- Raw input → Inbox/
