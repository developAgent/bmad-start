# Claude Template

Reusable instructions for carrying the progressive-disclosure development-history system into a new repository. Place below instructions into your CLAUDE.md if you want Claude to maintain a development history index and log. I find this useful for my own development workflow and as source material for writing AI building articles on my AI Substack https://ai.georgeliu.com.

## Goal

Keep a lightweight `CLAUDE-history.md` index in the repo root and store full narrative entries as separate files under `history/`. The index stays short and scannable; the detail lives in the linked entry files.

## Files to Create

```text
CLAUDE.md
AGENTS.md                       # if you keep a separate agent instruction file
CLAUDE-history.md
history/
  .counter
```

Initialize `history/.counter` with the next sequence number to use:

```text
1
```

## Block to Paste into `CLAUDE.md` or `AGENTS.md`

~~~~markdown
## Development History Requirement

**MANDATORY:** This project maintains a living development history. Use progressive disclosure: a lightweight index file plus individual entry files.

### Structure

```text
CLAUDE-history.md              # Index only -- one row per entry, links to files
history/
  .counter                     # Plain text integer, next sequence number to use
  2026-04-10_001_decision_initial-architecture.md
  2026-04-10_002_code-change_add-auth-flow.md
  ...
```

### What Gets Logged (Meaningful State Transitions Only)

The history should capture narrative-worthy moments, not mechanical edits. Before creating an entry, ask: "Would this be useful context in a retrospective, handoff, or public write-up about building this project?" If the answer is no, skip it.

**LOG these (meaningful state transitions):**
- A feature or tool reaching working state
- An architectural or implementation decision
- A bug or problem encountered, investigated, and resolved
- A new dependency added and why it was chosen
- A deployment attempt (success or failure)
- An unexpected discovery about a platform, API, or library
- A significant refactor that changes structure or design
- A configuration change that affects behavior
- A documentation change that materially improves onboarding, operation, or implementation clarity
- Batched related small changes as a single entry when together they represent one meaningful milestone

**DO NOT LOG these (mechanical noise):**
- Fixing a typo, formatting, or linting
- Renaming a variable or file without changing behavior
- Adding or removing imports only
- Adjusting whitespace, comments, or style only
- Intermediate saves while a feature is still in progress
- Retrying a command that failed due to a transient issue
- Reading files or researching without a resulting action

**When in doubt:** Batch related small changes into one entry rather than logging each one separately.

### Procedure for Creating a New Entry

1. Read `history/.counter` to get the next sequence number (for example `10`)
2. Create a new file: `history/YYYY-MM-DD_NNN_category_slug.md` where:
   - `YYYY-MM-DD` is today's date
   - `NNN` is the counter value, zero-padded to 3 digits (for example `010`)
   - `category` is one of: `code-change`, `decision`, `bug-fix`, `dependency`, `deployment`, `refactor`, `configuration`, `testing`, `documentation`, `discovery`
   - `slug` is a short kebab-case description
3. Write the entry file using this format:

```markdown
# YYYY-MM-DD HH:MM -- [Category]

**What:** Brief description of what happened
**Why:** Rationale or trigger for this change
**Details:** Technical details, decisions made, or relevant implementation notes
**Outcome:** Result or current state after this change
```

4. Append a new row to the appropriate table in `CLAUDE-history.md`:

```markdown
| NNN | YYYY-MM-DD | Category | One-line summary | [history/filename.md](history/filename.md) |
```

5. Increment `history/.counter` (for example `10` becomes `11`)
6. At the same checkpoint, review the high-signal docs most likely to have drifted and update them if needed. Typical examples include:
   - `README.md`
   - architecture / ADR / implementation docs
   - operator or runbook docs
   - `CLAUDE.md` / `AGENTS.md`

### When to Create an Entry

Create an entry at these natural checkpoints:
- A feature or tool is complete and working
- A decision is made that shapes the direction of the project
- A bug is fully resolved
- A deployment is attempted
- A surprising discovery is confirmed
- Before a git commit that represents a logical unit of work

At those checkpoints, also ask: "Did this change make any planning, onboarding, implementation, or operator docs inaccurate?" If yes, update those docs in the same unit of work.

### Important

- **Do NOT dump full details into `CLAUDE-history.md`** -- it is an index only
- **Do NOT read every history entry file by default** -- read the index first, then load individual entries on demand
- **Do NOT skip the counter increment** -- it prevents filename collisions
- **Do NOT treat docs as automatically current** -- meaningful changes should trigger a drift review
~~~~

## Starter `CLAUDE-history.md`

Use this if you want a phase-based index:

```markdown
# Development History: <repo-name>

> Index of development entries for this project. Each entry is a separate file in `history/`. This file is the lightweight reference -- read individual entries on demand for full details.

## How This Works

- This file is an **index only** -- one line per entry with a link to the full entry file
- Full entry content lives in `history/YYYY-MM-DD_NNN_category_slug.md`
- The counter at `history/.counter` tracks the next sequence number
- Claude should update this index whenever a new entry is created

---

## Phase 0: Planning

| # | Date | Category | Summary | File |
|---|------|----------|---------|------|

---

## Phase 1: Implementation

| # | Date | Category | Summary | File |
|---|------|----------|---------|------|
```

If the repo does not use phases, keep a single table instead:

```markdown
# Development History: <repo-name>

> Index of development entries for this project. Each entry is a separate file in `history/`. This file is the lightweight reference -- read individual entries on demand for full details.

| # | Date | Category | Summary | File |
|---|------|----------|---------|------|
```

## Starter Entry File

```markdown
# YYYY-MM-DD HH:MM -- [Category]

**What:** Brief description of what happened
**Why:** Why this work was done
**Details:** Technical detail, design choices, or relevant notes
**Outcome:** What changed or what the current state is now
```

## Suggested Setup Sequence for a New Repo

1. Create `CLAUDE-history.md`, `history/`, and `history/.counter`
2. Paste the development-history block into `CLAUDE.md`
3. Mirror the same block into `AGENTS.md` if you use one
4. Seed the index with either phased sections or a single-table layout
5. Start writing entries only when a meaningful checkpoint is reached

## Practical Defaults

- Keep the index human-scannable
- Prefer one strong entry over several tiny ones
- Use the entry files for context that would clutter the main index
- Treat documentation changes as history-worthy only when they materially change how someone builds, operates, or understands the project
