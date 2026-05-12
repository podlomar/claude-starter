# claude-starter

A personal template for new coding projects — pre-configured with Claude Code skills and subagent setups I've found most useful.

## What's included

### Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| `commit` | `/commit [all] [hint]` | Creates a git commit following a unified `<emoji> <type>: <message>` format. Pass `all` to auto-stage everything before committing. |

### Coming soon

Subagent configurations and additional skills will be added here as the template evolves.

## Using this template

1. Copy or clone this repo as the starting point for a new project
2. Remove `.git/` and re-initialize: `rm -rf .git && git init`
3. The `.claude/` directory carries over automatically — all skills and settings are immediately available in Claude Code

## Repository structure

```
.claude/
├── settings.json     # project-scoped Claude Code permissions
└── skills/
    └── commit/
        └── SKILL.md  # /commit skill definition
```

## Adding skills

Drop a new folder under `.claude/skills/<name>/` containing a `SKILL.md` file. Claude Code picks it up automatically — no registration needed.

Skill frontmatter reference:

```yaml
---
name: skill-name
description: >
  When to invoke this skill.
allowed-tools:
  - Bash(git status:*)
argument-hint: "[optional args]"
---
```

## Commit format

All commits in projects using this template follow:

```
<emoji> <type>: <message>
```

Examples:

```
✨ feat: add user authentication
🐛 fix: handle empty response from API
♻️ refactor: extract validation into helper
🔧 chore: upgrade dependencies
```

See [.claude/skills/commit/SKILL.md](.claude/skills/commit/SKILL.md) for the full type→emoji map and edge case handling.
