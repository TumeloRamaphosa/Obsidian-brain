---
name: second-brain
description: The master skill — captures, organizes, connects, and evolves knowledge across all StudEx operations
trigger: Always active. Guides how Claude interacts with the vault as a living knowledge system.
---

# Second Brain Skill — The Knowledge Operating System

This skill defines how Claude Code operates as the **intelligence layer** of the StudEx Obsidian vault. It's not just a note-taker — it's a thinking partner that captures, connects, and activates knowledge.

## The Second Brain Principles

1. **Capture Everything** — No insight lost. Every conversation, email, idea gets into the vault.
2. **Organize for Action** — Notes aren't filed away to die. They're structured to drive decisions.
3. **Connect Relentlessly** — Every note links to related notes. The graph IS the intelligence.
4. **Surface What Matters** — The right knowledge at the right time. Not a dump of everything.
5. **Evolve Continuously** — The brain gets smarter with every interaction. Never static.

## The Knowledge Lifecycle

```
┌──────────────────────────────────────────────────────────────┐
│                    THE SECOND BRAIN LOOP                      │
│                                                               │
│    ┌─────────┐    ┌──────────┐    ┌──────────┐               │
│    │ CAPTURE  │───▶│ ORGANIZE │───▶│ CONNECT  │               │
│    │          │    │          │    │          │               │
│    │ Chats    │    │ Classify │    │ Wikilink │               │
│    │ Emails   │    │ Tag      │    │ Cross-ref│               │
│    │ Files    │    │ Place    │    │ Backlink │               │
│    │ Ideas    │    │ Template │    │ Graph    │               │
│    └─────────┘    └──────────┘    └────┬─────┘               │
│                                        │                      │
│    ┌─────────┐    ┌──────────┐    ┌────▼─────┐               │
│    │ EVOLVE   │◀──│  ACT     │◀───│ RETRIEVE │               │
│    │          │    │          │    │          │               │
│    │ Update   │    │ Decide   │    │ RAG      │               │
│    │ Refine   │    │ Plan     │    │ Search   │               │
│    │ Archive  │    │ Execute  │    │ Recall   │               │
│    │ Grow     │    │ Build    │    │ Rank     │               │
│    └─────────┘    └──────────┘    └──────────┘               │
└──────────────────────────────────────────────────────────────┘
```

## How to Operate as the Second Brain

### On Every Interaction

1. **Ground yourself** — Read soul.md to know who you're working for and why
2. **Check context** — What business entity is this about? What recent activity is relevant?
3. **Think in links** — Every piece of information connects to something. Find the connection.
4. **Capture as you go** — If the user shares something new, offer to add it to the vault
5. **Close loops** — If an action item is completed, mark it done. If a decision is made, log it.

### When New Information Arrives

```
New info ──→ Is it already in the vault?
                │
                ├── YES → Update existing note, add new details
                │
                └── NO  → Does it deserve its own note?
                           │
                           ├── YES → Create note with full frontmatter,
                           │         place in correct folder, link to related notes
                           │
                           └── NO  → Add to an existing note as a section or bullet point
```

### When Asked a Question

```
Question ──→ Search vault (RAG skill)
                │
                ├── Found relevant notes → Synthesize answer, cite sources
                │
                └── Gaps found → Answer what you can, flag what's missing,
                                 suggest what to capture next
```

### When Making Decisions

Every decision should be:
1. **Logged** — Add to the relevant business note or create a decision note
2. **Tagged** — `#decision`
3. **Linked** — Connect to the business entity and any related notes
4. **Action-ized** — What needs to happen next? Create `- [ ]` items tagged `#action-item`

## Multi-Device Sync Strategy

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Machine 1   │     │   Machine 2   │     │   Phone/Web  │
│  Claude Code  │     │  Claude Code  │     │  claude.ai   │
│  + Obsidian   │     │  + Obsidian   │     │  /code       │
└──────┬───────┘     └──────┬───────┘     └──────┬───────┘
       │                     │                     │
       └─────────┬──────────┘─────────────────────┘
                 │
          ┌──────▼──────┐
          │   GitHub     │
          │  Obsidian-   │
          │  brain repo  │
          └─────────────┘
```

### Sync Workflow
1. **Before working**: `git pull origin main` — get latest from all devices
2. **While working**: Claude Code reads/writes vault files directly
3. **After working**: `git add . && git commit && git push` — share changes
4. **On phone**: Use claude.ai/code against the GitHub repo, or Obsidian Git plugin

### Conflict Resolution
- If two devices edit the same note, git merge handles it
- For frontmatter conflicts, prefer the most recently modified version
- For content conflicts, keep both versions and reconcile manually

## Knowledge Graph Health Metrics

Periodically assess the brain's health:

| Metric | Healthy | Warning | Action |
|--------|---------|---------|--------|
| Orphan notes (no links) | 0 | >5 | Run vault-organizer agent |
| Stale notes (>30 days) | <10% | >30% | Review and update or archive |
| Inbox backlog | 0 files | >10 files | Run /project:process-inbox |
| Action items overdue | 0 | >5 | Review and prioritize |
| Missing frontmatter | 0 | Any | Fix immediately |

## Integration Map

```
second-brain (this skill — the orchestrator)
├── rag skill         — Searches and retrieves vault knowledge
├── chat-processor    — Ingests new conversations
├── business-analyzer — Generates strategic analysis
├── daily-digest      — Logs daily progress
├── vault-organizer   — Maintains knowledge graph
├── chat-scraper      — Multi-platform extraction
└── business-analyst  — Revenue and strategy analysis
```

## The Feedback Loop That Makes It Work

The brain gets smarter because:
1. **Every chat you have with ANY AI** → gets exported → processed → added to vault
2. **Every question you ask Claude Code** → reveals what matters → improves future retrieval
3. **Every decision logged** → builds a decision history → better future advice
4. **Every daily log** → creates a timeline → enables "what happened this week/month/year"
5. **Every business analysis** → updates strategy → directs next actions

This is not a static wiki. It's a **compounding knowledge machine**.
