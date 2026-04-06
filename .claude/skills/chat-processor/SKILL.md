---
name: chat-processor
description: Automatically processes new chat exports dropped into Inbox/chats/
trigger: When files are added to Inbox/chats/ subdirectories
---

# Chat Processor Skill

When new files appear in any Inbox/chats/ subdirectory, this skill activates to process them.

## Workflow

1. Detect the source platform from the subdirectory name (chatgpt, gemini, claude, etc.)
2. Parse the file format (JSON, markdown, or plain text)
3. For each conversation found:
   a. Extract the date, topic, and key content
   b. Classify by business relevance: [[StudEx Group]], [[StudEx Meat]], [[StudEx Global Markets]], [[StudEx DevOps]], or general
   c. Extract action items, decisions, and insights
   d. Create a structured note in the appropriate Notes/ subfolder
   e. Add wikilinks to related existing notes
4. Update [[Chat Processing Log]]
5. Report summary to user

## Note Template for Processed Chats

```markdown
---
title: <Topic>
tags: [chat-extract, <business-tag>, <topic-tags>]
created: <today>
modified: <today>
source: <platform>
chat_date: <original-date>
---

# <Topic>

## Summary
<2-3 sentence summary>

## Key Points
- Point 1
- Point 2

## Action Items
- [ ] Action 1 #action-item
- [ ] Action 2 #action-item

## Insights
<Business-relevant insights>

## Source
Extracted from <platform> conversation on <date>.
Original file: Inbox/chats/<platform>/<filename>

## Related
- [[related note 1]]
- [[related note 2]]
```
