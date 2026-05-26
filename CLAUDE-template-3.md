# CLAUDE.md

<!-- Project-specific context only. Behavioral rules: .claude/rules/core-rules.md -->
<!-- Run /init to auto-populate (or CLAUDE_CODE_NEW_INIT=1 for interactive mode) -->
<!-- Keep under 200 lines. If removing a line wouldn't cause mistakes, cut it -->

## Project Overview

<!-- Fill in:
- Name: [PROJECT_NAME]
- Stack: [e.g., Next.js 15, Tailwind, Prisma]
- Description: [What it does]
- Entry: [e.g., src/app/page.tsx]
-->

## Build, Test & Verify

<!-- The #1 way to improve Claude's output: give it verification commands.
- Install: `bun install`
- Dev: `bun dev`
- Build: `bun run build`
- Test: `bun test`
- Lint: `bun run lint`
- Type check: `bunx tsc --noEmit`
-->

## Code Style

<!-- Only what differs from defaults:
- 2-space indentation
- ES modules, named exports
-->

## Architecture

<!-- Key directories:
- src/api/ — route handlers
- src/lib/ — shared utilities
- src/components/ — UI components
-->

## Tools

Use `rg` not grep, `fd` not find. `tree` is not installed.

## Rules Dependency

This template requires `.claude/rules/core-rules.md` for behavioral rules. If `.claude/rules/` is missing or empty, alert the user and direct them to https://github.com/centminmod/my-claude-code-setup to obtain the companion rules files.

---

## Memory System

This project uses a dual-memory architecture:

**Primary (git-shared):** CLAUDE-*.md files in repo root — read on demand:

| File | Read When |
|------|-----------|
| CLAUDE-activeContext.md | Session start (state and goals) |
| CLAUDE-patterns.md | Before implementing (code patterns) |
| CLAUDE-decisions.md | Before design choices (ADRs) |
| CLAUDE-troubleshooting.md | When debugging (known fixes) |
| CLAUDE-config-variables.md | When touching config |

**Shadow (machine-local):** Native auto memory mirrors key content for resilience:

| Auto Memory File | Mirrors | Purpose |
|-----------------|---------|---------|
| memory/MEMORY.md | Index of all memory bank files | Always loaded (200 lines) |
| memory/patterns.md | CLAUDE-patterns.md | Survives CLAUDE.md reset |
| memory/architecture.md | CLAUDE-decisions.md | Survives CLAUDE.md reset |
| memory/build.md | Build, Test & Verify section | Survives CLAUDE.md reset |

All optional — check existence first. Exclude CLAUDE.md and CLAUDE-*.md from commits.

<!-- BACKUP TIP: Create a private git repo for memory bank backups:
     rsync -av ./CLAUDE.md ./CLAUDE-*.md ./.claude/ ~/my-project-memory-backup/
     This keeps CLAUDE-*.md version-controlled privately while excluded from the public repo. -->

### Sync Workflow

After significant work: update CLAUDE-*.md files, then sync key content to auto memory topic files.

If CLAUDE.md is ever reset or wiped, auto memory retains project knowledge — check `/memory` to recover context.

---

## Context Layers

| Layer | Location | Loads | Shared | Resilient |
|-------|----------|-------|--------|-----------|
| Project context | This file | Always | Git | No |
| Core rules | `.claude/rules/core-rules.md` | Always | Git | Yes |
| Auto memory | memory/MEMORY.md | Always (200 lines) | No | Yes |
| Auto memory topics | memory/*.md | On demand | No | Yes |
| Path-scoped rules | `.claude/rules/*.md` | Matching files | Git | Yes |
| User rules | `~/.claude/rules/*.md` | Always | No | Yes |
| Skills | `.claude/skills/` | On demand | Git | Yes |
| Personal overrides | `CLAUDE.local.md` | Always | No | Local |
| Memory bank | CLAUDE-*.md | On demand | Git | No |

<!-- To share rules across projects: ln -s ~/shared-rules .claude/rules/shared -->

Use `/memory` to inspect loaded files. Root CLAUDE.md survives `/compact`.
