# CLAUDE.md

<!-- Run /init to auto-populate (or CLAUDE_CODE_NEW_INIT=1 for interactive setup) -->
<!-- Keep under 200 lines. If removing a line wouldn't cause mistakes, cut it -->
<!-- HTML comments like these are stripped from context — free for maintainer notes -->

## Project Overview

<!-- Fill in what Claude can't discover from reading code:
- Name: [PROJECT_NAME]
- Stack: [e.g., Next.js 15, Tailwind, Prisma]
- Description: [What this project does]
- Entry: [e.g., src/app/page.tsx]
-->

## Build, Test & Verify

<!-- The #1 way to improve Claude's output: give it verification commands.
- Install: `bun install`
- Dev: `bun dev`
- Build: `bun run build`
- Test (all): `bun test`
- Test (single): `bun test path/to/test`
- Lint: `bun run lint`
- Type check: `bunx tsc --noEmit`
-->

## Code Style

<!-- Only rules that differ from language defaults:
- 2-space indentation
- ES module imports (not CommonJS)
- Prefer named exports
-->

## Architecture

<!-- Key directories and data flow:
- src/api/ — route handlers
- src/lib/ — shared utilities
- src/components/ — UI components
-->

---

## Rules

- **Investigate first:** Never speculate about code you have not read. Read files and ripgrep for usages before making claims. If uncertain, say so and propose how to verify
- **Scope to the request:** Do what is asked; nothing more. When ambiguous, default to research and recommendations — only edit when explicitly asked. Do not refactor adjacent code or create abstractions for a single use
- **Verify before done:** Re-check each requirement. Run tests and lint. State what changed, what was verified, and what could not be
- **File discipline:** Edit existing files in place. Do not create new files unless required. Clean up scratch files
- **Safety:** Ask before destructive actions (deleting files/branches, force pushes, hard resets, --no-verify)
- **Efficiency:** Parallelize independent tool calls; serialize dependent ones
- **Tools:** Use `rg` not grep, `fd` not find. `tree` is not installed

---

## Memory Bank

This project uses CLAUDE-*.md files to retain context across sessions. Read only what your current task needs:

| File | Read When |
|------|-----------|
| CLAUDE-activeContext.md | Session start — current state and goals |
| CLAUDE-patterns.md | Before implementing — code patterns |
| CLAUDE-decisions.md | Before design choices — architecture ADRs |
| CLAUDE-troubleshooting.md | When debugging — known issues and fixes |
| CLAUDE-config-variables.md | When touching config |

All optional — check existence first. Exclude CLAUDE.md and CLAUDE-*.md from commits. Update after significant work (new patterns, decisions, fixes).

<!-- BACKUP TIP: Create a private git repo for memory bank backups:
     rsync -av ./CLAUDE.md ./CLAUDE-*.md ./.claude/ ~/my-project-memory-backup/
     This keeps CLAUDE-*.md version-controlled privately while excluded from the public repo. -->

### Memory Resilience

When updating memory bank files, also sync key information into native auto memory (`~/.claude/projects/` memory directory). This dual-layer approach ensures project knowledge survives even if CLAUDE.md is reset:

- **MEMORY.md index:** Maintain pointers to which CLAUDE-*.md files exist and their current topics
- **Auto memory topic files:** Mirror critical patterns, architecture decisions, and build commands into memory topic files (e.g., `memory/patterns.md`, `memory/architecture.md`)
- **Core rules:** After learning behavioral preferences from corrections, save them as auto memory entries so they persist independently

This way, a fresh session after a CLAUDE.md wipe still has project context via auto memory.

---

## Context Layers

| Layer | Location | Loads | Survives CLAUDE.md Reset |
|-------|----------|-------|--------------------------|
| Core rules & project context | This file | Always | No — rebuild from auto memory |
| Auto memory index | `~/.claude/projects/.../memory/MEMORY.md` | Always (first 200 lines) | Yes |
| Auto memory topics | `~/.claude/projects/.../memory/*.md` | On demand | Yes |
| Path-scoped rules | `.claude/rules/*.md` | When matching files | Yes (separate files) |
| User-level rules | `~/.claude/rules/*.md` | Always | Yes (separate files) |
| Skills & workflows | `.claude/skills/` | On demand via `/skill-name` | Yes (separate files) |
| Personal overrides | `CLAUDE.local.md` | Always (gitignored) | Depends on file |
| Memory bank | CLAUDE-*.md | On demand | No — mirrored to auto memory |

Use `/memory` to see which files are loaded in your session.
