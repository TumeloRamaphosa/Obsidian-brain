---
title: Multi-Device Sync Guide
tags: [system, setup, devops, studex]
created: 2026-04-08
modified: 2026-04-08
aliases: [sync-guide, multi-device, setup]
---

# Multi-Device Sync Guide

> How to access and update the StudEx Second Brain from any device.

## The Problem

Claude Desktop sessions are isolated per machine. Claude Code on Machine A can't see what Claude Code did on Machine B. Your brain needs to be everywhere.

## The Solution: Git Is Your Sync Layer

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Desktop #1   │     │  Desktop #2   │     │  Phone/Web   │
│  Claude Code  │     │  Claude Code  │     │  claude.ai   │
│  + Obsidian   │     │  + Obsidian   │     │  /code       │
└──────┬───────┘     └──────┬───────┘     └──────┬───────┘
       │                     │                     │
       └────────────┬────────┘─────────────────────┘
                    │
             ┌──────▼──────┐
             │   GitHub     │
             │  Obsidian-   │
             │  brain repo  │
             └─────────────┘
```

## Setup Per Machine

### 1. Clone the Vault
```bash
git clone https://github.com/TumeloRamaphosa/Obsidian-brain.git
cd Obsidian-brain
```

### 2. Open in Obsidian
- Open Obsidian → "Open folder as vault" → select the cloned repo
- Obsidian settings (`.obsidian/`) are gitignored — each machine has its own

### 3. Open in Claude Code
```bash
cd Obsidian-brain
claude
```
Claude Code automatically reads `CLAUDE.md` and `.claude/` config. All commands, skills, and agents are immediately available.

### 4. Daily Workflow
```bash
# Start of session — pull latest
git pull origin main

# Work with Claude Code (notes are created/updated)
# ...

# End of session — push changes
git add -A
git commit -m "Session update — [brief description]"
git push origin main
```

## Access Methods

### Option A: Claude Code CLI (Desktop)
Best for deep work. Full file access, all skills available.
```bash
cd Obsidian-brain && claude
```

### Option B: Claude Code Web (claude.ai/code)
Works from any browser. Connects to the GitHub repo directly.
- Go to claude.ai/code
- Connect your GitHub account
- Open the Obsidian-brain repo
- All commands and skills work the same

### Option C: Claude Projects (claude.ai)
For quick queries without full vault access.
- Create a project on claude.ai
- Upload key files as project knowledge: `soul.md`, business profiles, CLAUDE.md
- Chat with Claude using your business context
- Less powerful than Code, but accessible from anywhere

### Option D: Obsidian Git Plugin (Mobile/Desktop)
For Obsidian app users who want auto-sync.
- Install the "Obsidian Git" community plugin
- Configure with your GitHub credentials
- Auto-pull on open, auto-push on close
- Works on mobile (iOS/Android) with iSH or Termux

## Handling Chat Exports from Different Machines

### Machine 1 (Work laptop)
```bash
# Export ChatGPT conversations → drop in Inbox/chats/chatgpt/
# Export Gemini conversations → drop in Inbox/chats/gemini/
git add Inbox/ && git commit -m "Add chat exports from work laptop" && git push
```

### Machine 2 (Home desktop)
```bash
git pull  # Get the chat exports from Machine 1
claude    # Open Claude Code
# Run /project:process-inbox to process everything
```

### Phone
- Copy/paste chat snippets into a .md file
- Push via Obsidian Git plugin or GitHub mobile app
- Process later from any machine with Claude Code

## Keeping the Brain Fresh

| Frequency | Action | Command |
|-----------|--------|---------|
| Every session | Pull latest, push when done | `git pull` / `git push` |
| Daily | Create daily log | `/project:daily-log` |
| When chats pile up | Process inbox | `/project:process-inbox` |
| Weekly | Generate weekly summary | `/project:weekly-summary` |
| Monthly | Full business analysis | `/project:analyze-business` |

## Related Notes

- [[soul]]
- [[StudEx DevOps]]
- [[Chat Processing Log]]
