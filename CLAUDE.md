# CLAUDE.md — StudEx Group Obsidian Second Brain

## Repository Overview

This is the **StudEx Group Obsidian Second Brain** — a knowledge management operating system that powers the StudEx business ecosystem. It connects to Claude Code via the `.claude/` configuration for AI-powered workflows.

**Owner:** Tumelo Ramaphosa — see [[soul]] for full identity and vision.

## Architecture: The Memory Stack

```
┌──────────────────────────────────────────────────────┐
│  ACCESS — Claude Code / OpenClaw                     │
│  Query vault from anywhere — terminal, phone, web    │
├──────────────────────────────────────────────────────┤
│  CONTEXT — /project:recall                           │
│  Temporal + topic modes — loads what matters NOW      │
├──────────────────────────────────────────────────────┤
│  SEARCH — Grep/Glob + vault structure                │
│  Fast retrieval — find anything in < 1s              │
├──────────────────────────────────────────────────────┤
│  DATA — This Obsidian Vault                          │
│  Notes, sessions, transcripts, daily logs            │
│  Your second brain on disk                           │
└──────────────────────────────────────────────────────┘
```

## Repository Structure

```
Obsidian-brain/
├── CLAUDE.md                          # This file — AI assistant guide
├── soul.md                            # Root identity — founder vision & business map
├── .gitignore                         # Ignores .obsidian/, local configs
│
├── Notes/                             # Core knowledge base
│   ├── Businesses/
│   │   ├── StudEx-Group/              # Holding company
│   │   ├── StudEx-Meat/               # Agriculture, genetics, meat
│   │   ├── StudEx-Global-Markets/     # International trade, export
│   │   └── StudEx-DevOps/             # Technology, AI, consulting
│   ├── Projects/                      # Active projects
│   ├── Content/                       # Content creation
│   ├── People/                        # People / CRM
│   ├── Topics/                        # Knowledge topics
│   ├── Ideas/                         # Unvalidated ideas
│   └── Meetings/                      # Meeting notes
│
├── Inbox/                             # Unprocessed raw content
│   ├── chats/                         # AI conversation exports
│   │   ├── chatgpt/
│   │   ├── gemini/
│   │   ├── claude/
│   │   ├── perplexity/
│   │   ├── manus/
│   │   ├── minimax/
│   │   ├── qwen/
│   │   └── ollama/
│   ├── emails/                        # Email captures
│   └── files/                         # Raw documents
│
├── Daily/                             # Daily logs
│   └── weekly/                        # Weekly summaries
│
├── Sessions/                          # Claude conversation logs
│
├── Templates/                         # Note templates
│   ├── daily-log.md
│   ├── meeting-note.md
│   ├── business-plan.md
│   ├── project-note.md
│   ├── person.md
│   ├── email-summary.md
│   └── chat-extract.md
│
└── .claude/                           # Claude Code control center
    ├── settings.json                  # Permissions & config (committed)
    ├── commands/                      # Custom slash commands
    │   ├── recall.md                  # → /project:recall
    │   ├── process-inbox.md           # → /project:process-inbox
    │   ├── analyze-business.md        # → /project:analyze-business
    │   ├── daily-log.md               # → /project:daily-log
    │   ├── weekly-summary.md          # → /project:weekly-summary
    │   └── search.md                  # → /project:search
    ├── rules/                         # Modular instruction files
    │   ├── vault-conventions.md       # Frontmatter, tags, linking rules
    │   ├── note-style.md              # Writing tone and format
    │   └── organization.md            # Folder placement, business hierarchy
    ├── skills/                        # Auto-invoked workflows
    │   ├── chat-processor/SKILL.md    # Process chat exports → vault notes
    │   ├── business-analyzer/SKILL.md # Deep business analysis
    │   └── daily-digest/SKILL.md      # End-of-day summary
    └── agents/                        # Subagent personas
        ├── business-analyst.md        # Revenue analysis, strategy
        ├── vault-organizer.md         # Knowledge graph maintenance
        └── chat-scraper.md            # Multi-platform chat extraction
```

## The StudEx Business Ecosystem

```
soul.md (root identity)
├── [[StudEx Group]]           — Holding company
│   ├── [[StudEx Meat]]        — Premium genetics, breeding, meat production
│   ├── [[StudEx Global Markets]] — International trade, commodities, export
│   └── [[StudEx DevOps]]      — AI, development, consulting, infrastructure
```

**Every business note MUST connect back to one of these entities.**

## Key Conventions

### File Formats
- All notes are **Markdown** (`.md`) files
- **YAML frontmatter** is required (between `---` delimiters)
- Internal links use **wikilink syntax**: `[[Note Name]]` or `[[Note Name|Display Text]]`
- Note names use **Title Case**

### Required Frontmatter
```yaml
---
title: Note Title
tags: [relevant, tags]
created: YYYY-MM-DD
modified: YYYY-MM-DD
---
```

### Tag Taxonomy
- `#studex` — Core StudEx content
- `#business` — Business-related
- `#action-item` — Actionable task
- `#idea` — Unvalidated idea
- `#research` — Research content
- `#decision` — Decision record
- `#meeting` — Meeting notes
- `#chat-extract` — Extracted from AI conversation

### Linking Rules
- ALWAYS use `[[wikilinks]]` to connect related notes
- Business notes MUST link to their parent entity
- Every note should link to at least one other note (no orphans)
- NEVER break existing wikilinks

## Workflow: Chat-to-Knowledge Pipeline

```
All AI Chats ──→ Inbox/chats/<platform>/ ──→ /project:process-inbox ──→ Organized Notes
                                                     │
Gmail ──→ Inbox/emails/ ────────────────────────────┘
Local Files ──→ Inbox/files/ ───────────────────────┘
                                                     │
                                                     ▼
                                         Notes/ (classified by business)
                                         Action Items (#action-item)
                                         [[Chat Processing Log]] updated
```

## Custom Commands Reference

| Command | What It Does |
|---------|-------------|
| `/project:recall <topic>` | Search vault and synthesize everything known about a topic |
| `/project:process-inbox` | Scan Inbox/, extract knowledge, create organized notes |
| `/project:analyze-business` | Full business health assessment and revenue ranking |
| `/project:daily-log` | Create today's daily log entry |
| `/project:weekly-summary` | Summarize the past 7 days |
| `/project:search <query>` | Deep search across the entire vault |

## Important Warnings

- **Do NOT modify `.obsidian/`** unless explicitly asked
- **Do NOT delete notes** without explicit permission
- **Do NOT restructure folders** without permission
- **Preserve all existing `[[wikilinks]]`** — broken links degrade the knowledge graph
- **Never delete Inbox files** — they are source-of-truth archives

## Obsidian Syntax Reference

| Feature | Syntax |
|---------|--------|
| Internal link | `[[Note Name]]` |
| Link with alias | `[[Note Name\|Display Text]]` |
| Embed note | `![[Note Name]]` |
| Embed image | `![[image.png]]` |
| Block reference | `[[Note Name#^block-id]]` |
| Heading link | `[[Note Name#Heading]]` |
| Tag | `#tag` or `#nested/tag` |
| Callout | `> [!note]` / `> [!warning]` / `> [!tip]` |
| Task | `- [ ] task` / `- [x] done` |
| Comment | `%% hidden comment %%` |

## Git Practices
- Branch from `main` for changes
- Use clear, descriptive commit messages
- Push with `git push -u origin <branch-name>`
