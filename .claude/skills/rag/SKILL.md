---
name: rag
description: Retrieval-Augmented Generation — search vault, build context, generate answers
trigger: When Claude needs to answer questions using vault knowledge, or when user asks about any StudEx topic
---

# RAG Skill — Retrieval-Augmented Generation for StudEx Vault

This skill turns the Obsidian vault into a live knowledge base that Claude can query, reason over, and generate answers from. Every answer is grounded in YOUR notes, YOUR conversations, YOUR decisions.

## How It Works

```
Query ──→ RETRIEVE ──→ RANK ──→ AUGMENT ──→ GENERATE ──→ Answer + Sources
              │           │          │            │
              ▼           ▼          ▼            ▼
         Search vault  Score by   Build rich   Generate answer
         (Grep+Glob)   relevance  context      citing [[sources]]
```

## Retrieval Pipeline

### Step 1: Query Expansion
When given a question, expand it into multiple search vectors:
- **Exact terms** — The literal words used
- **Synonyms** — Related terms (e.g., "genetics" → "breeding", "semen", "embryos", "pedigree")
- **Business mapping** — Which entity does this relate to? ([[StudEx Meat]], [[StudEx Global Markets]], [[StudEx DevOps]], [[StudEx Group]])
- **Tag inference** — Which tags would relevant notes have? (#business, #research, #decision, etc.)

### Step 2: Multi-Strategy Search
Execute these searches in parallel:
1. **Grep content** — Search note bodies for keywords and phrases
2. **Glob filenames** — Find notes whose titles match the query
3. **Tag search** — Find notes with relevant tags in frontmatter
4. **Link graph** — Follow [[wikilinks]] from matched notes to discover connected knowledge
5. **Temporal search** — Check recent Daily/ logs and Sessions/ for fresh context

### Step 3: Rank & Filter
Score each retrieved note by:
- **Relevance** — How closely does it match the query?
- **Freshness** — When was it last modified? (recent = higher weight)
- **Authority** — Business profiles and soul.md rank higher than raw inbox
- **Connectivity** — Notes with more [[wikilinks]] are usually more important
- **Business alignment** — Does it connect to a StudEx entity?

### Step 4: Context Assembly
Build the context window:
1. Always include `soul.md` (identity grounding)
2. Include relevant business profile(s)
3. Add top-ranked notes (up to 10)
4. Add relevant action items and decisions
5. Add any recent daily logs mentioning the topic

### Step 5: Generate Answer
Produce an answer that:
- Directly answers the question
- Cites sources as [[wikilinks]]
- Flags gaps ("The vault doesn't have info on X yet")
- Suggests follow-up actions
- Identifies if any Inbox/ files might contain unprocessed relevant info

## The RAG Loop — Keeping Knowledge Fresh

```
┌──────────────────────────────────────────────────┐
│                 THE RAG LOOP                      │
│                                                   │
│  1. CAPTURE — Drop chats/files into Inbox/        │
│       │                                           │
│       ▼                                           │
│  2. PROCESS — /project:process-inbox              │
│       │         Extract knowledge → create notes  │
│       ▼                                           │
│  3. RETRIEVE — RAG skill searches vault           │
│       │         Finds relevant knowledge          │
│       ▼                                           │
│  4. REASON — Claude analyzes and connects         │
│       │         Generates insights + actions      │
│       ▼                                           │
│  5. ACT — Execute on insights                     │
│       │     Create business plans, make decisions │
│       ▼                                           │
│  6. LOG — Daily digest captures what happened     │
│       │                                           │
│       └──────→ Back to step 1 (new conversations) │
└──────────────────────────────────────────────────┘
```

## Usage Examples

**"What do we know about meat export to the Middle East?"**
→ Searches vault → finds StudEx Meat notes, StudEx Global Markets notes, any processed chats about export → synthesizes answer with [[sources]]

**"What decisions have we made this week?"**
→ Searches daily logs, notes with #decision tag, recent git commits → compiles decision log

**"What's the most profitable opportunity right now?"**
→ Pulls all business profiles, revenue streams, action items → ranks by ROI using business-analyst agent logic

## Auto-Update Triggers

The vault stays fresh through:
1. **New chats processed** → /project:process-inbox adds new knowledge
2. **Daily logs** → /project:daily-log captures daily progress
3. **Weekly summaries** → /project:weekly-summary rolls up the week
4. **Business analysis** → /project:analyze-business re-evaluates strategy
5. **Git sync** → Pull from other devices to merge knowledge from all machines

## Integration with Other Skills

| Skill | How RAG Uses It |
|-------|----------------|
| chat-processor | RAG searches notes created by chat processing |
| business-analyzer | RAG feeds data to the analyzer, analyzer feeds insights back |
| daily-digest | RAG includes daily logs in temporal searches |
| second-brain | Second Brain skill calls RAG for context when creating new notes |
