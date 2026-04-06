# CLAUDE.md - AI Assistant Guide for Obsidian-brain

## Repository Overview

This is an **Obsidian vault** — a personal knowledge management system built on interconnected Markdown files. Obsidian uses a local-first approach where all notes are plain-text `.md` files organized in folders with rich interlinking via `[[wikilinks]]`.

## Repository Structure

```
Obsidian-brain/
├── CLAUDE.md              # This file — AI assistant guidelines
├── .obsidian/             # Obsidian app configuration (themes, plugins, settings)
└── (vault content)        # Markdown notes, folders, and attachments
```

## Key Conventions

### File Formats
- All notes are **Markdown** (`.md`) files
- Obsidian uses **YAML frontmatter** for metadata (between `---` delimiters at the top of files)
- Internal links use **wikilink syntax**: `[[Note Name]]` or `[[Note Name|Display Text]]`
- Attachments (images, PDFs) may live in a dedicated folder (e.g., `attachments/`, `assets/`, or `_resources/`)

### Linking and Organization
- **Wikilinks** (`[[...]]`) are the primary way notes connect to each other — preserve and respect existing links
- **Tags** use `#tag` syntax in the note body or `tags:` in frontmatter
- **Aliases** can be defined in frontmatter for alternative note names
- Folder structure reflects topic hierarchy — follow existing patterns when adding content

### Frontmatter Template
```yaml
---
title: Note Title
tags: [topic1, topic2]
created: YYYY-MM-DD
modified: YYYY-MM-DD
aliases: [alternate-name]
---
```

## Development Workflow

### Git Practices
- Branch from `main` for changes
- Use clear, descriptive commit messages
- Push with `git push -u origin <branch-name>`

### When Modifying Notes
1. **Read before editing** — understand the note's context and links before making changes
2. **Preserve wikilinks** — never break `[[existing links]]` between notes
3. **Follow existing structure** — match the folder hierarchy, naming conventions, and frontmatter format already in use
4. **Respect templates** — if template notes exist (often in a `Templates/` folder), use them for new notes
5. **Keep attachments organized** — place images/files in the designated attachments folder

### When Creating New Notes
- Match the naming convention of existing notes (e.g., Title Case, kebab-case, etc.)
- Include appropriate frontmatter metadata
- Add `[[wikilinks]]` to connect the new note to related existing notes
- Place the note in the correct folder based on its topic

## Important Warnings

- **Do NOT modify `.obsidian/`** configuration files unless explicitly asked — these control the user's app settings, themes, and plugin configurations
- **Do NOT delete notes** without explicit permission — knowledge vaults contain interconnected information where removing one note can break links across many others
- **Do NOT restructure folders** without permission — the user's organizational system is intentional
- **Preserve all existing links** — broken wikilinks degrade the vault's knowledge graph

## Obsidian-Specific Syntax Reference

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
