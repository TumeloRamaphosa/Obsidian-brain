---
title: Inbox — How to Use
tags: [system, inbox, processing]
created: 2026-04-06
modified: 2026-04-06
---

# Inbox

This is where raw, unprocessed content lands before Claude Code organizes it into the vault.

## Folder Structure

```
Inbox/
├── chats/
│   ├── chatgpt/      # Export from ChatGPT (JSON or Markdown)
│   ├── gemini/        # Export from Google Gemini
│   ├── manus/         # Export from Manus AI
│   ├── perplexity/    # Export from Perplexity
│   ├── minimax/       # Export from MiniMax
│   ├── qwen/          # Export from Qwen
│   ├── ollama/        # Export from Ollama (local)
│   └── claude/        # Export from Claude conversations
├── emails/            # Email captures
└── files/             # Raw files, documents, PDFs
```

## How to Add Chats

1. **ChatGPT**: Settings → Data Controls → Export Data → extract `.json` → drop in `chats/chatgpt/`
2. **Gemini**: Use Google Takeout → extract conversations → drop in `chats/gemini/`
3. **Claude**: Copy conversation or use API export → drop in `chats/claude/`
4. **Perplexity**: Copy threads as markdown → drop in `chats/perplexity/`
5. **Others**: Export or copy-paste conversations as `.md` or `.json` files

## Processing

Run `/project:process-inbox` to have Claude Code:
1. Scan all new files in Inbox/
2. Extract key topics, decisions, and action items
3. Create structured notes in the appropriate vault location
4. Link to relevant business entities ([[StudEx Group]], [[StudEx Meat]], [[StudEx Global Markets]])
5. Update [[Chat Processing Log]]

## File Naming Convention

Use: `YYYY-MM-DD_source_topic.md` (e.g., `2026-04-06_chatgpt_meat-export-strategy.md`)
