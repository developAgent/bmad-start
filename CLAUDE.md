# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **BMad Method** (Behavior-driven Method for Agentic Development) project template — a framework for AI-driven development providing complete tooling across the software development lifecycle: analysis, planning, solutioning, and implementation.

## Key Commands

- `/bmad-help` — Primary help command; shows where you are in the workflow and recommends next steps
- `/bmad-product-brief` — Define product idea in a brief
- `/bmad-prfaq` — PRFAQ Working Backwards challenge for product concept stress-testing
- `/bmad-brainstorming` — Expert-guided ideation facilitation
- `/bmad-create-prd` — Create Product Requirements Document
- `/bmad-sprint-planning` — Generate sprint status from epics

## Architecture

### Skills System

Skills are stored in `.claude/skills/` as markdown files with YAML frontmatter (`name`, `description`). Each skill is a self-contained workflow that can be invoked via `/<skill-name>`.

**Skill naming convention**:
- `bmad-*` — BMad Method core skills
- `bmad-bmb-*` — Builder module skills (creating/extending BMad components)
- `bmad-gds-*` — Game Dev Studio module skills
- `bmad-cis-*` — Creative Intelligence Suite module skills
- `bmad-testarch-*` — Test Architecture Enterprise module skills

### Module Organization

```
_bmad/                          # Module configurations and manifests
  _config/
    bmad-help.csv              # Master skill catalog (all modules)
    manifest.yaml              # Installed modules registry
  core/                         # Core module (built-in)
  bmb/                          # Builder module
  gds/                          # Game Dev Studio module
  cis/                          # Creative Intelligence Suite
  tea/                          # Test Architecture Enterprise
.claude/skills/                 # All skill definitions
  bmad-*/                       # BMad Method skills
  gds-*/                        # GDS skills
  gds-agent-*/                  # GDS agent roles
  bmad-cis-*/                   # CIS skills
  bmad-testarch-*/              # TEA skills
_bmad-output/                   # Generated artifacts (PRDs, specs, etc.)
```

### Workflow Phases

BMad Method flows through phases (phase names vary by module):
1. `1-analysis` / `1-preproduction` — Research, market analysis, domain expertise
2. `2-planning` / `2-design` — Brief, PRD, UX design
3. `3-solutioning` / `3-technical` — Architecture, epics & stories
4. `4-implementation` / `4-production` — Development, testing, deployment

### Output Locations

Configured per-module in `_bmad/<module>/config.yaml`. Default output folder is `_bmad-output/`. Key paths:
- `planning_artifacts` — PRD, architecture, research
- `implementation_artifacts` — stories, sprint status
- `bmad_builder_reports` — Builder module reports
- `project_knowledge` — Generated project context documentation

### Skill Catalog

`_bmad/_config/bmad-help.csv` is the authoritative registry of all skills. Columns include: `module`, `skill`, `phase`, `required`, `after`, `before`, `outputs`. This CSV drives `/bmad-help` recommendations.

### Multi-Agent Skill Structure

Some skills use agent subdirectories (e.g., `gds-agent-tech-writer/`) containing role-specific documentation like `documentation-standards.md` and `explain-concept.md`.

## Module Documentation URLs

- BMad Method: https://docs.bmad-method.org/llms.txt
- BMad Builder: https://bmad-builder-docs.bmad-method.org/llms.txt
- Game Dev Studio: https://game-dev-studio-docs.bmad-method.org/llms.txt
- Test Architecture: https://bmad-code-org.github.io/bmad-method-test-architecture-enterprise/llms.txt
- Creative Intelligence Suite: https://cis-docs.bmad-method.org/llms.txt
