# CLAUDE.md

<!-- Keep under 200 lines. If removing a line wouldn't cause mistakes, cut it -->
<!-- HTML comments like these are stripped from context at runtime — free for humans -->
<!-- First-time setup: run /init (or CLAUDE_CODE_NEW_INIT=1 for interactive mode) -->

## Project Overview

<!-- Fill in what Claude can't discover from code:
- Project Name: [NAME]
- Tech Stack: [e.g., Next.js, Python/FastAPI, Go]
- Description: [What this project does]
- Entry Point: [e.g., src/index.ts, main.py]
-->

## Build, Test & Verify

<!-- The single highest-leverage thing: give Claude verification commands.
- Install: `bun install` / `pnpm install`
- Dev: `bun dev`
- Build: `bun run build`
- Test (all): `bun test`
- Test (single): `bun test path/to/test`
- Lint: `bun run lint`
- Type check: `bunx tsc --noEmit`
-->

## Code Style & Conventions

<!-- Only rules that differ from language defaults:
- 2-space indentation
- ES module imports (not CommonJS)
- Prefer named exports
-->

## Architecture

<!-- Key directories and purpose:
- src/api/ — route handlers
- src/lib/ — shared utilities
- src/components/ — UI components
-->

---

## Core Rules

**Investigation & accuracy:**
- Never speculate about code you have not read. Read files and ripgrep for usages before making claims
- If the user references a file, read it before answering
- If uncertain, say so and propose how to verify. Do not fabricate APIs, paths, or behavior

**Scope discipline:**
- Do what has been asked; nothing more, nothing less
- When intent is ambiguous, default to research and recommendations — only edit when explicitly asked
- Make only the changes requested. Do not refactor adjacent code, add docstrings to unchanged code, or create abstractions for a single use
- Follow scoping words ("only", "just", "exactly") literally

**Verification & safety:**
- Before declaring done: re-check requirements, run tests and lint, state what changed and what you could not verify
- Ask before destructive or hard-to-reverse actions: deleting files/branches, force pushes, hard resets, --no-verify
- Edit existing files in place. Do not create new files unless required. Clean up scratch files

**Efficiency & tools:**
- Parallelize independent tool calls; serialize dependent ones
- Use `rg` not grep, `fd` not find. `tree` is not installed

---

## Memory Bank System

This project uses a dual-memory architecture for maximum resilience:

1. **CLAUDE-*.md files** (git-tracked, team-shared) — the primary memory bank
2. **Native auto memory** (machine-local, per-project) — a persistent shadow that survives CLAUDE.md resets

### Memory Bank Files

Read on demand — only load what your current task needs:

| File | Purpose | Read When |
|------|---------|-----------|
| CLAUDE-activeContext.md | Session state, goals, progress | Always first at session start |
| CLAUDE-patterns.md | Code patterns and conventions | Before implementing features |
| CLAUDE-decisions.md | Architecture decisions (ADRs) | Before design choices |
| CLAUDE-troubleshooting.md | Known issues and proven solutions | When debugging |
| CLAUDE-config-variables.md | Configuration variables reference | When touching config |
| CLAUDE-temp.md | Temporary scratch pad | Only when explicitly referenced |

All files are optional — check existence before reading.

### Memory Bank Workflow

1. **Session start:** Read CLAUDE-activeContext.md for continuity
2. **During work:** Read other context files as needed
3. **After significant work:** Update relevant CLAUDE-*.md files (new patterns, decisions, fixes)
4. **Sync to auto memory:** Mirror key updates into native auto memory topic files:
   - `memory/MEMORY.md` — index of memory bank files and their current state
   - `memory/patterns.md` — established code patterns (mirrors CLAUDE-patterns.md)
   - `memory/architecture.md` — architecture decisions (mirrors CLAUDE-decisions.md)
   - `memory/build-and-test.md` — build commands and verification steps
   - `memory/troubleshooting.md` — known issues (mirrors CLAUDE-troubleshooting.md)

When asked to commit, exclude CLAUDE.md and CLAUDE-*.md from commits.

### Why Dual Memory

| Aspect | CLAUDE-*.md (Memory Bank) | Auto Memory (MEMORY.md) |
|--------|---------------------------|------------------------|
| Shared via git | Yes | No (machine-local) |
| Survives CLAUDE.md wipe | No | Yes |
| Survives `/init` re-run | No (may be overwritten) | Yes |
| Team members see it | Yes | No (personal) |
| Auto-loaded at session start | No (on demand) | Yes (first 200 lines) |
| Topic files on demand | N/A | Yes |

The memory bank is your team's shared truth. Auto memory is your personal safety net.

### Backups

When asked to backup, copy CLAUDE.md, CLAUDE-*.md files, and `.claude/` settings to the specified backup directory.

<!-- BACKUP STRATEGY FOR MAINTAINERS:
     Create a separate private git repo locally for memory bank backups:
       mkdir ~/my-project-memory-backup && cd ~/my-project-memory-backup && git init
     Then sync/rsync CLAUDE-*.md files there on a schedule or after updates:
       rsync -av /path/to/project/CLAUDE.md /path/to/project/CLAUDE-*.md ~/my-project-memory-backup/
       rsync -av /path/to/project/.claude/ ~/my-project-memory-backup/.claude/
       cd ~/my-project-memory-backup && git add -A && git commit -m "memory bank sync $(date)"
     Push to a private remote (GitHub/GitLab private repo) for off-machine backup.
     This keeps memory bank content version-controlled privately while CLAUDE-*.md
     in the main public repo remain excluded from commits via .gitignore. -->

---

## Progressive Disclosure

| Layer | Location | Loads | Resilient |
|-------|----------|-------|-----------|
| Core rules & overview | This file | Always | Git-tracked |
| Auto memory index | MEMORY.md | Always (200 lines) | Machine-local |
| Auto memory topics | memory/*.md | On demand | Machine-local |
| Path-scoped rules | `.claude/rules/*.md` | When matching files | Git-tracked |
| User-level rules | `~/.claude/rules/*.md` | Always | Machine-local |
| Skills & workflows | `.claude/skills/` | On demand | Git-tracked |
| Personal overrides | `CLAUDE.local.md` | Always (gitignored) | Local only |
| Memory bank files | CLAUDE-*.md | On demand | Git-tracked |

Use `/memory` to see which files are loaded. Root CLAUDE.md survives `/compact`; subdirectory CLAUDE.md files reload when Claude next reads files there.

Path-scoped rules in `.claude/rules/` are optional — core rules are inline above. For path-scoped rule examples, see https://github.com/centminmod/my-claude-code-setup.

For libraries/frameworks, verify current APIs via Context7 MCP before implementing.
