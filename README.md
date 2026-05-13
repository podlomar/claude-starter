# claude-starter

A personal template for new coding projects — pre-configured with Claude Code skills, guidelines, and tooling configs.

## Using this template

1. Clone or copy this repo into your new project
2. Remove `.git/` and re-initialize: `rm -rf .git && git init`
3. The `.claude/` directory carries over automatically

## What's included

**Skills** — invoke with `/skill-name` in Claude Code:

| Skill | Trigger | Description |
|-------|---------|-------------|
| `commit` | `/commit [all] [hint]` | Commits staged changes using `<emoji> <type>: <message>` format. `all` auto-stages everything first. |

**Guidelines** — loaded automatically via `CLAUDE.md`:

| File | Description |
|------|-------------|
| [coding-guide.md](.claude/guidelines/coding-guide.md) | Language-independent rules: comments |
| [js-style-guide.md](.claude/guidelines/js-style-guide.md) | JS/TS rules: functions, async, boolean expressions, linting suppressions |
| [react-style-guide.md](.claude/guidelines/react-style-guide.md) | React rules: state management |

**Templates** — copy into new projects as needed:

| File | Description |
|------|-------------|
| [biome.json](templates/biome.json) | Formatter + linter aligned with the JS style guide |
| [tsconfig.json](templates/tsconfig.json) | Strict TypeScript with `noImplicitReturns`, `noUncheckedIndexedAccess` |

## Permissions

[`.claude/settings.json`](.claude/settings.json) pre-configures safe defaults:

- **Allow** — read-only ops, git inspection, `npm run`, `gh pr/issue view/list/status`
- **Ask** — `git push/pull/merge/rebase`, `gh pr create/merge`, `gh issue create/close`, `env`/`set`
- **Deny** — `rm -rf`, `git push --force`, `sudo`, SSH/SCP, secrets files (`.env`, `*.key`, `*.pem`, …)

## Extending

- **New skill**: add `.claude/skills/<name>/SKILL.md`
- **New guideline**: add `.claude/guidelines/<name>.md` and reference it in `CLAUDE.md`
