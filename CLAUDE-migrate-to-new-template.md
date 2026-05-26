# CLAUDE.md Migration Guide

<!-- This file is an AI prompt. Paste its contents (or reference it) when asking Claude Code to migrate your existing CLAUDE.md to a new template. -->

## How to Use This Guide

1. Choose a target template (see comparison below)
2. Tell Claude Code:

```
Read CLAUDE-migrate-to-new-template.md and my current CLAUDE.md. Migrate my CLAUDE.md to Template [1|2|3], preserving all my project-specific content.
```

---

## Template Comparison

| Aspect | Template 1 | Template 2 | Template 3 |
|--------|-----------|-----------|-----------|
| **File** | [`CLAUDE-template-1.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-1.md) | [`CLAUDE-template-2.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-2.md) | [`CLAUDE-template-3.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-3.md) |
| **Lines** | ~101 | ~153 | ~105 |
| **Philosophy** | Compact self-contained | Memory bank headline + dual memory | Progressive disclosure native |
| **Rules location** | Inline bullets | Inline grouped sections | External `.claude/rules/core-rules.md` |
| **Memory system** | Table + resilience section | Full workflow + dual-memory comparison | Dual-table (primary + shadow) |
| **External deps** | None | None (optional `.claude/rules/`) | Requires [`.claude/rules/core-rules.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/.claude/rules/core-rules.md) |
| **Best for** | Quick starts, small projects | Existing memory bank users | Teams wanting max context efficiency |

---

## Migration Instructions for AI

<!-- Everything below is structured as an AI-readable prompt. When an AI assistant reads this file, it should follow these instructions to perform the migration. -->

### Step 1: Analyze the User's Existing CLAUDE.md

Read the user's current `CLAUDE.md` and extract:

1. **Project Overview** — name, stack, description, entry point
2. **Build/Test/Verify commands** — install, dev, build, test, lint, type-check
3. **Code style rules** — indentation, imports, naming conventions
4. **Architecture** — key directories and their purposes
5. **Custom rules** — any behavioral instructions not in the chosen template
6. **Tool preferences** — rg/fd/jq usage, banned tools
7. **Memory bank references** — which CLAUDE-*.md files exist and are referenced
8. **Platform-specific docs** — CLAUDE-cloudflare.md, CLAUDE-convex.md, etc.
9. **Backup instructions** — any custom backup workflows
10. **Other custom sections** — anything unique to the user's project

### Step 2: Choose Target Template

If the user hasn't specified, recommend based on their existing setup:

- **Heavy memory bank user** (many CLAUDE-*.md files, update workflow) → Template 2
- **Team project or context-sensitive** (many rules, large codebase) → Template 3
- **Simple project or getting started** → Template 1

### Step 3: Migrate Content

Read the chosen template file and populate it. If the template files are not in the local project, fetch them from:

- [`CLAUDE-template-1.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-1.md)
- [`CLAUDE-template-2.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-2.md)
- [`CLAUDE-template-3.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/CLAUDE-template-3.md)
- [`.claude/rules/core-rules.md`](https://github.com/centminmod/my-claude-code-setup/raw/refs/heads/master/.claude/rules/core-rules.md) (required for Template 3)

#### For All Templates

1. **Replace HTML comment placeholders** with the user's actual project info:
   - `<!-- Fill in: Name, Stack, Description, Entry -->` → user's project overview
   - `<!-- The #1 way to improve... -->` → user's actual build/test commands
   - `<!-- Only rules that differ... -->` → user's code style rules
   - `<!-- Key directories... -->` → user's architecture

2. **Preserve custom rules** the user has added beyond the template defaults. Add them under the appropriate section (Rules, Code Style, or Architecture).

3. **Keep memory bank file references** that the user already has. If they have additional CLAUDE-*.md files beyond the template defaults (e.g., `CLAUDE-cloudflare.md`, `CLAUDE-convex.md`), add them to the memory bank table.

4. **Preserve tool preferences** beyond the default `rg`/`fd` line. If the user has custom tool configs, add them.

5. **Keep backup instructions** if the user has customized them.

#### Template-Specific Steps

**Template 1** (Compact Self-Contained):
- All rules go as inline bullets under `## Rules`
- Memory bank is a simple table under `## Memory Bank`
- Memory resilience section is brief — keep it concise

**Template 2** (Memory Bank System):
- Rules go under grouped headings: Investigation & accuracy, Scope discipline, Verification & safety, Efficiency & tools
- Memory bank workflow section should reflect the user's actual workflow
- Dual-memory comparison table stays as-is
- Add user's backup preferences to the Backups section

**Template 3** (Progressive Disclosure Native):
- Rules go in `.claude/rules/core-rules.md` (create or update this file)
- CLAUDE.md stays lean — project context only
- Copy `.claude/rules/core-rules.md` from this repo if it doesn't exist
- Add any custom rules to core-rules.md under the appropriate section
- The "Rules Dependency" section must remain — it alerts if .claude/rules/ is missing

### Step 4: Handle Removed Content

Some content from old CLAUDE.md formats should NOT be migrated:

- **100-line rg/fd/jq reference blocks** → replaced by single line: `Use rg not grep, fd not find. tree is not installed.`
- **`@` prefixed file references** → remove `@` prefix; memory bank files are read on-demand, not auto-loaded
- **Duplicated rules from `~/.claude/CLAUDE.md`** → templates are standalone; include rules inline or in .claude/rules/
- **AGENTS.md references** → tool preferences are now inline; AGENTS.md is no longer needed as a dependency
- **`tree` command usage** → tree is not installed; use `fd` instead

### Step 5: Validate Migration

After generating the new CLAUDE.md:

1. **Line count check**: Should be under 200 lines (ideally under 150)
2. **Pruning test**: For each line, ask "would removing this cause mistakes?" — if not, cut it
3. **No `@` imports**: Memory bank files should NOT have `@` prefix (progressive disclosure)
4. **HTML comments**: Use `<!-- -->` for template guidance — zero runtime token cost
5. **Completeness**: All user's project-specific content is preserved
6. **No fabrication**: Don't invent project details not in the original CLAUDE.md

### Step 6: Post-Migration Setup

After writing the new CLAUDE.md:

1. **For Template 3 users**: Verify `.claude/rules/core-rules.md` exists. If not, copy from this repo or create it with the user's behavioral rules.

2. **Memory bank files**: Existing CLAUDE-*.md files (CLAUDE-activeContext.md, CLAUDE-patterns.md, etc.) continue to work unchanged with all templates.

3. **Auto memory sync**: On first session with the new CLAUDE.md, update native auto memory to mirror the new structure:
   - `memory/MEMORY.md` — index of memory bank files
   - `memory/patterns.md` — mirror of CLAUDE-patterns.md
   - `memory/architecture.md` — mirror of CLAUDE-decisions.md

4. **Test the migration**: Run `/init` to verify Claude Code reads the new CLAUDE.md correctly.

---

## Example Migration

**Before** (old format, 250+ lines):
```markdown
# CLAUDE.md

## AI Guidance
* ALWAYS read and understand relevant files...
* After receiving tool results...
[50 lines of behavioral rules]

## ALWAYS START WITH THESE COMMANDS
[100 lines of rg/fd/jq reference]

## Memory Bank System
@CLAUDE-activeContext.md
@CLAUDE-patterns.md
[...]
```

**After** (Template 1, ~80 lines):
```markdown
# CLAUDE.md

## Project Overview
- Name: my-app
- Stack: Next.js 15, Tailwind, Prisma
- Description: E-commerce platform
- Entry: src/app/page.tsx

## Build, Test & Verify
- Install: `bun install`
- Build: `bun run build`
- Test: `bun test`
- Lint: `bun run lint`

## Rules
- Investigate first: Never speculate about code you have not read...
- Scope to the request: Do what is asked; nothing more...
[compact behavioral rules as bullets]

## Tools
Use `rg` not grep, `fd` not find. `tree` is not installed.

## Memory Bank
| File | Read When |
|------|-----------|
| CLAUDE-activeContext.md | Session start |
| CLAUDE-patterns.md | Before implementing |
[...]
```

---

## Frequently Asked Questions

**Q: Do I lose my CLAUDE-*.md memory bank files?**
A: No. All existing CLAUDE-*.md files (activeContext, patterns, decisions, etc.) work unchanged with all three templates. Only the root CLAUDE.md is migrated.

**Q: Can I switch between templates later?**
A: Yes. Templates only change how CLAUDE.md is structured. Your memory bank files, .claude/ settings, and auto memory are all independent.

**Q: What if I have custom sections in my CLAUDE.md?**
A: The migration preserves all project-specific content. Custom sections are placed under the most appropriate heading in the new template.

**Q: Do I need `.claude/rules/core-rules.md` for Templates 1 and 2?**
A: No. Templates 1 and 2 have rules inline. The rules file is only required for Template 3, but any template can optionally use it for rules that should load based on file paths.

**Q: What about `@` imports I currently use?**
A: Remove them. The new templates use progressive disclosure — memory bank files are read on-demand when needed, not auto-loaded with `@`. This saves context window tokens.
