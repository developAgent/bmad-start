# BMad Method Skills Catalog

BMad (Behavior-driven Method for Agentic Development) provides a comprehensive set of skills organized into modules. Each skill is a self-contained workflow invoked via `/<skill-name>`.

---

## Table of Contents

- [Core Module](#core-module)
- [BMad Method Module](#bmad-method-module)
- [BMad Builder Module](#bmad-builder-module)
- [Game Dev Studio Module](#game-dev-studio-module)
- [Creative Intelligence Suite Module](#creative-intelligence-suite-module)
- [Test Architecture Enterprise Module](#test-architecture-enterprise-module)

---

## Core Module

Core utilities for documentation, reviews, and collaboration.

| Command | Display Name | Description | Phase |
|---------|-------------|-------------|-------|
| `bmad-brainstorming` | Brainstorming | Use early in ideation or when stuck generating ideas. | anytime |
| `bmad-party-mode` | Party Mode | Orchestrate multi-agent discussions when you need multiple perspectives or want agents to collaborate. | anytime |
| `bmad-help` | BMad Help | Get help navigating the BMad workflow. | anytime |
| `bmad-index-docs` | Index Docs | Use when LLM needs to understand available docs without loading everything. | anytime |
| `bmad-shard-doc` | Shard Document | Use when doc becomes too large (>500 lines) to manage effectively. | anytime |
| `bmad-editorial-review-prose` | Editorial Review - Prose | Use after drafting to polish written content. | anytime |
| `bmad-editorial-review-structure` | Editorial Review - Structure | Use when doc produced from multiple subprocesses or needs structural improvement. | anytime |
| `bmad-review-adversarial-general` | Adversarial Review | Use for quality assurance or before finalizing deliverables. | anytime |
| `bmad-review-edge-case-hunter` | Edge Case Hunter Review | Use alongside adversarial review for orthogonal coverage — method-driven not attitude-driven. | anytime |
| `bmad-distillator` | Distillator | Use when you need token-efficient distillates that preserve all information for downstream LLM consumption. | anytime |

---

## BMad Method Module

The main BMad Method workflow for product development.

### Phase 1: Analysis

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-brainstorming` | Brainstorm Project | Expert guided facilitation through a single or multiple techniques. |
| `bmad-market-research` | Market Research | Market analysis competitive landscape customer needs and trends. |
| `bmad-domain-research` | Domain Research | Industry domain deep dive subject matter expertise and terminology. |
| `bmad-technical-research` | Technical Research | Technical feasibility architecture options and implementation approaches. |
| `bmad-product-brief` | Create Brief | An expert guided experience to nail down your product idea in a brief. |
| `bmad-prfaq` | PRFAQ Challenge | Working Backwards guided experience to forge and stress-test your product concept. |

### Phase 2: Planning

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-create-prd` | Create PRD | Expert led facilitation to produce your Product Requirements Document. |
| `bmad-validate-prd` | Validate PRD | Validate an existing PRD against standards. |
| `bmad-edit-prd` | Edit PRD | Improve and enhance an existing PRD. |
| `bmad-create-ux-design` | Create UX | Guidance through realizing the plan for your UX. |

### Phase 3: Solutioning

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-create-architecture` | Create Architecture | Guided workflow to document technical decisions. |
| `bmad-create-epics-and-stories` | Create Epics and Stories | Create the Epics and Stories listing from PRD requirements. |
| `bmad-check-implementation-readiness` | Check Implementation Readiness | Ensure PRD UX Architecture and Epics Stories are aligned. |

### Phase 4: Implementation

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-sprint-planning` | Sprint Planning | Kicks off implementation by producing a plan the implementation agents will follow. |
| `bmad-sprint-status` | Sprint Status | Anytime: Summarize sprint status and route to next workflow. |
| `bmad-create-story` | Create Story | Story cycle start: Prepare first found story in the sprint plan. |
| `bmad-create-story validate` | Validate Story | Validates story readiness and completeness before development work begins. |
| `bmad-dev-story` | Dev Story | Story cycle: Execute story implementation tasks and tests. |
| `bmad-code-review` | Code Review | Story cycle: If issues back to DS if approved then next CS or ER if epic complete. |
| `bmad-checkpoint-preview` | Checkpoint | Guided walkthrough of a change from purpose and context into details. |
| `bmad-qa-generate-e2e-tests` | QA Automation Test | Generate automated API and E2E tests for implemented code. |
| `bmad-retrospective` | Retrospective | Optional at epic end: Review completed work lessons learned. |

### Anytime / Cross-Phase

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-document-project` | Document Project | Analyze an existing project to produce useful documentation. |
| `bmad-generate-project-context` | Generate Project Context | Scan existing codebase to generate a lean LLM-optimized project-context.md. |
| `bmad-quick-dev` | Quick Dev | Unified intent-in code-out workflow: clarify plan implement review and present. |
| `bmad-correct-course` | Correct Course | Navigate significant changes. May recommend start over update PRD redo architecture sprint planning or correct epics and stories. |

### Tech Writer Agent Skills

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-agent-tech-writer write` | Write Document | Describe in detail what you want, and the agent will follow documentation best practices. |
| `bmad-agent-tech-writer update-standards` | Update Standards | Update agent memory documentation-standards.md with your specific preferences. |
| `bmad-agent-tech-writer mermaid` | Mermaid Generate | Create a Mermaid diagram based on user description. |
| `bmad-agent-tech-writer validate` | Validate Document | Review the specified document against documentation standards and best practices. |
| `bmad-agent-tech-writer explain` | Explain Concept | Create clear technical explanations with examples and diagrams for complex concepts. |

---

## BMad Builder Module

Build and extend the BMad framework itself.

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-bmb-setup` | Setup Builder Module | Install or update BMad Builder module config and help entries. |
| `bmad-agent-builder` | Build an Agent | Create, edit, or rebuild an agent skill through conversational discovery. |
| `bmad-agent-builder` (quality-analysis) | Analyze an Agent | Run quality analysis on an existing agent — structure, cohesion, prompt craft, and enhancement opportunities. |
| `bmad-workflow-builder` | Build a Workflow | Create, edit, or rebuild a workflow or utility skill. |
| `bmad-workflow-builder` (quality-analysis) | Analyze a Workflow | Run quality analysis on an existing workflow/skill. |
| `bmad-workflow-builder` (convert-process) | Convert a Skill | Convert any skill to BMad-compliant, outcome-driven equivalent. |
| `bmad-module-builder` | Ideate Module | Brainstorm and plan a BMad module — explore ideas, decide architecture, and produce a build plan. |
| `bmad-module-builder` | Create Module | Scaffold module infrastructure into built skills, making them an installable BMad module. |
| `bmad-module-builder` | Validate Module | Check that a module's structure is complete, accurate, and all capabilities are properly registered. |

---

## Game Dev Studio Module

Specialized workflow for game development.

### Phase 1: Preproduction

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-brainstorm-game` | Brainstorm Game | Facilitate game brainstorming sessions with game-specific context and techniques. |
| `gds-market-research` | Market Research | Game market analysis competitive landscape player needs and trends. |
| `gds-domain-research` | Domain Research | Game industry domain deep dive subject matter expertise and terminology. |
| `gds-technical-research` | Technical Research | Technical feasibility game engine options and implementation approaches. |
| `gds-create-game-brief` | Game Brief | Interactive game brief creation that guides users through defining their game vision. |

### Phase 2: Design

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-create-gdd` | Game Design Document | Create a GDD with mechanics systems progression and implementation guidance. |
| `gds-validate-gdd` | Validate GDD | Validate an existing GDD against standards. |
| `gds-edit-gdd` | Edit GDD | Improve and enhance an existing GDD. |
| `gds-create-narrative` | Narrative Design | Create comprehensive narrative documentation including story structure character arcs and world-building. |
| `gds-create-ux-design` | Create UX Design | Guidance through realizing the plan for your game UX/UI. |
| `gds-create-prd` | Create PRD | Create a PRD from GDD or from scratch. |
| `gds-validate-prd` | Validate PRD | Validate PRD against standards for external tool compatibility. |
| `gds-edit-prd` | Edit PRD | Improve and enhance an existing PRD. |

### Phase 3: Technical

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-generate-project-context` | Project Context | Create optimized project-context.md for chosen agentic tool consistency. |
| `gds-game-architecture` | Game Architecture | Produce a scale-adaptive game architecture with engine systems networking and technical design. |
| `gds-create-epics-and-stories` | Create Epics and Stories | Create the Epics and Stories listing from GDD requirements. |
| `gds-check-implementation-readiness` | Check Implementation Readiness | Ensure GDD UX Architecture and Epics Stories are aligned before production begins. |
| `gds-test-framework` | Test Framework | Initialize game test framework architecture for Unity Unreal Engine or Godot projects. |
| `gds-test-design` | Test Design | Create comprehensive game test scenarios covering gameplay progression and quality requirements. |

### Phase 4: Production

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-sprint-planning` | Sprint Planning | Generate or update sprint-status.yaml from epic files. |
| `gds-sprint-status` | Sprint Status | View sprint progress surface risks and get next action recommendation. |
| `gds-create-story` | Create Story | Create Story with comprehensive context for developer agent implementation. |
| `gds-dev-story` | Dev Story | Execute Dev Story workflow implementing tasks and tests. |
| `gds-code-review` | Code Review | Perform thorough clean context QA code review on stories flagged Ready for Review. |
| `gds-retrospective` | Retrospective | Facilitate team retrospective after a game development epic is completed. |

### Game Test Workflow

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-test-automate` | Test Automate | Generate automated game tests. |
| `gds-e2e-scaffold` | E2E Scaffold | Scaffold E2E testing infrastructure. |
| `gds-playtest-plan` | Playtest Plan | Create structured playtesting plan. |
| `gds-performance-test` | Performance Test | Design performance testing strategy. |
| `gds-test-review` | Test Review | Review test quality and coverage. |

### Anytime / Cross-Phase

| Command | Display Name | Description |
|---------|-------------|-------------|
| `gds-document-project` | Document Project | Analyze an existing game project to produce useful documentation. |
| `gds-quick-prototype` | Quick Prototype | Rapid game prototyping to test mechanics and ideas quickly. |
| `gds-quick-dev` | Quick Dev | Clarify plan implement review and present any user intent or change request in a single workflow. |
| `gds-correct-course` | Correct Course | Navigate significant changes during game dev sprint when implementation is off-track. |

---

## Creative Intelligence Suite Module

Cognitive tools for ideation, design thinking, and innovation.

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-brainstorming` | Brainstorming | Facilitate brainstorming sessions using one or more techniques. |
| `bmad-cis-design-thinking` | Design Thinking | Guide human-centered design processes using empathy-driven methodologies. |
| `bmad-cis-innovation-strategy` | Innovation Strategy | Identify disruption opportunities and architect business model innovation. |
| `bmad-cis-problem-solving` | Problem Solving | Apply systematic problem-solving methodologies to crack complex challenges. |
| `bmad-cis-storytelling` | Storytelling | Craft compelling narratives using proven story frameworks and techniques. |

---

## Test Architecture Enterprise Module

Enterprise-grade test architecture and automation.

### Learning

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-teach-me-testing` | Teach Me Testing | Teach testing fundamentals through 7 sessions (TEA Academy). |

### Phase 3: Solutioning

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-testarch-test-design` | Test Design | Risk-based test planning. |
| `bmad-testarch-framework` | Test Framework | Initialize production-ready test framework. |
| `bmad-testarch-ci` | CI Setup | Configure CI/CD quality pipeline. |

### Phase 4: Implementation

| Command | Display Name | Description |
|---------|-------------|-------------|
| `bmad-testarch-atdd` | ATDD | Generate red-phase acceptance test scaffolds before implementation. |
| `bmad-testarch-automate` | Test Automation | Expand test coverage. |
| `bmad-testarch-test-review` | Test Review | Quality audit (0-100 scoring). |
| `bmad-testarch-nfr` | NFR Assessment | Non-functional requirements assessment. |
| `bmad-testarch-trace` | Traceability | Coverage traceability and gate. |

---

## Skill Naming Convention

Skills follow this naming pattern:

| Prefix | Module |
|--------|--------|
| `bmad-*` | BMad Method core skills |
| `bmad-bmb-*` | Builder module skills (creating/extending BMad components) |
| `bmad-gds-*` | Game Dev Studio module skills |
| `bmad-cis-*` | Creative Intelligence Suite module skills |
| `bmad-testarch-*` | Test Architecture Enterprise module skills |
| `gds-*` | Game Dev Studio shorthand |

---

## Module Documentation URLs

- BMad Method: https://docs.bmad-method.org/llms.txt
- BMad Builder: https://bmad-builder-docs.bmad-method.org/llms.txt
- Game Dev Studio: https://game-dev-studio-docs.bmad-method.org/llms.txt
- Test Architecture: https://bmad-code-org.github.io/bmad-method-test-architecture-enterprise/llms.txt
- Creative Intelligence Suite: https://cis-docs.bmad-method.org/llms.txt