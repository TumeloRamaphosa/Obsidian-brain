---
name: daily-digest
description: Generates end-of-day summary of all vault activity
trigger: On demand via /project:daily-log
---

# Daily Digest Skill

Creates a daily log entry summarizing all vault activity and business progress.

## Workflow

1. Check git log for today's file changes
2. Read any new or modified notes
3. Check for completed and outstanding action items
4. Compile into daily log format
5. Save to Daily/YYYY-MM-DD.md

## Daily Log Template

```markdown
---
title: Daily Log — YYYY-MM-DD
tags: [daily, log]
created: YYYY-MM-DD
---

# Daily Log — Day, Month DD, YYYY

## Today's Focus
- Primary objective for the day

## What Happened
- Notes created/modified
- Chats processed
- Decisions made

## Action Items
### Completed
- [x] Item

### Outstanding
- [ ] Item #action-item

## Business Pulse
- [[StudEx Group]] — update
- [[StudEx Meat]] — update
- [[StudEx Global Markets]] — update
- [[StudEx DevOps]] — update

## Insights
- Key takeaway from today

## Tomorrow's Priority
- What to focus on next
```
