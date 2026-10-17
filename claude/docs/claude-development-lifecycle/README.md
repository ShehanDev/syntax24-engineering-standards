# Claude Code Development Lifecycle Cookbook

A practical, step-by-step command cookbook covering the complete software development lifecycle using Claude Code. Every command, skill, plugin, and prompt documented here has been verified against the actual capabilities installed in this Claude Code environment.

## Overview

This cookbook documents what actually exists in your environment — not what we wish existed. It covers:

| Category | What you'll find |
|----------|------------------|
| Built-in Claude Code commands | `claude agents`, `claude mcp`, `claude plugin`, `claude doctor`, `claude ultrareview`, `claude update`, etc. |
| Available skills | 25 skills from the `agent-skills@addy-agent-skills` plugin |
| Design skills | `ui-ux-pro-max` suite (banner, brand, design, design-system, slides, ui-styling, ui-ux-pro-max) |
| Reference plugins | `awesome-design`, `linkedin-skills`, `claude-mem-cowork` |
| Natural-language prompts | Prompts that instruct Claude Code to perform tasks when no dedicated command exists |

## Directory Structure

```
docs/claude-development-lifecycle/
├── README.md                          # This file — overview and how to use
├── 01-project-discovery.md            # Phase 1: Project discovery and repository analysis
├── 02-requirements-and-specification.md # Phase 2: Idea refinement and requirements
├── 03-ui-ux-and-design.md             # Phase 3: UI/UX and design
├── 04-architecture-and-technical-planning.md # Phase 4: Architecture and technical planning
├── 05-task-breakdown.md               # Phase 5: Task breakdown and implementation planning
├── 06-implementation.md               # Phase 6: Implementation
├── 07-testing-and-quality-assurance.md # Phase 7: Testing and quality assurance
├── 08-code-review-and-refactoring.md   # Phase 8: Code review and refactoring
├── 09-security-and-performance.md      # Phase 9: Security and performance
├── 10-deployment-and-release.md        # Phase 10: Deployment and release
├── 11-maintenance-and-debugging.md     # Phase 11: Maintenance and debugging
├── 12-session-handoff.md               # Phase 12: Session handoff
├── COMMANDS-QUICK-REFERENCE.md         # Consolidated quick-reference table
└── SKILL-AND-PLUGIN-MAPPING.md         # Skill-to-phase mapping table
```

## Verified Available Skills and Plugins

### Agent-Skills Plugin (`agent-skills@addy-agent-skills`, v0.6.12)

| Skill | Supported Phases |
|-------|------------------|
| `idea-refine` | Phase 2 — Idea refinement |
| `spec-driven-development` | Phases 2, 4, 5 — Specs, architecture, task breakdown |
| `planning-and-task-breakdown` | Phase 5 — Task breakdown |
| `frontend-ui-engineering` | Phase 3, 6 — UI/UX and frontend implementation |
| `api-and-interface-design` | Phase 4, 6 — API design, interface contracts |
| `test-driven-development` | Phase 7 — Testing |
| `code-review-and-quality` | Phase 8 — Code review |
| `code-simplification` | Phase 8 — Refactoring |
| `security-and-hardening` | Phase 9 — Security |
| `performance-optimization` | Phase 9 — Performance |
| `debugging-and-error-recovery` | Phase 11 — Debugging |
| `shipping-and-launch` | Phase 10 — Deployment/release |
| `ci-cd-and-automation` | Phase 10 — CI/CD pipelines |
| `documenting-and-adrs` | All phases — Documentation, ADRs |
| `context-engineering` | All phases — Context/rules setup |
| `source-driven-development` | All phases — Verify against official docs |
| `incremental-implementation` | Phase 6 — Incremental implementation |
| `git-workflow-and-versioning` | All phases — Git workflow |
| `observability-and-instrumentation` | Phase 9, 10 — Monitoring |
| `deprecation-and-migration` | Phase 4, 10 — Migrations |
| `doubt-driven-development` | All phases — Question-driven refinement |
| `interview-me` | Phase 2 — Requirements gathering via interview |
| `browser-testing-with-devtools` | Phase 7, 11 — Browser-based testing |
| `using-agent-skills` | Meta-skill — How to use skills |

### UI/UX Pro Max Plugin (`ui-ux-pro-max@ui-ux-pro-max-skill`)

| Sub-skill | Supported Phases |
|-----------|------------------|
| `banner-design` | Phase 3 — UI design |
| `brand` | Phase 3 — Branding |
| `design` | Phase 3 — Design |
| `design-system` | Phase 3 — Design system |
| `slides` | Phase 3 — Presentations |
| `ui-styling` | Phase 3 — UI styling |
| `ui-ux-pro-max` | Phase 3 — UI/UX |

### Reference Plugins

| Plugin | Supported Phases | Notes |
|--------|------------------|-------|
| `awesome-design@awesome-design-skill` | Phase 3 | Design tokens for 74 brands |
| `linkedin-skills@linkedin-skills` | Not lifecycle-related | Social content |
| `claude-mem-cowork@thedotmack` | Phase 12 | Memory/search across sessions |

### Not Available (checked, not installed)

| Requested Item | Status |
|----------------|--------|
| `spec-driven-development` slash command | No dedicated slash command — invoke via Skill tool |
| `test-driven-development` slash command | No dedicated slash command — invoke via Skill tool |
| `code-review-and-quality` slash command | No dedicated slash command — invoke via Skill tool |
| `ui-ux-pro-max` slash command | No dedicated slash command — invoke via Skill tool |
| `awesome-design` slash command | No dedicated slash command — invoke via Skill tool |

Skills are invoked through the **Skill tool** (e.g., `Skill({ skill: "spec-driven-development" })`), not via slash commands. There are no dedicated slash commands for any of the installed skills.

## How to Use This Cookbook

1. **Find your phase** — Open the markdown file matching your current development phase.
2. **Read Purpose and Required Inputs** — Confirm you have what you need before starting.
3. **Use verified commands** — Each section labels commands as VERIFIED CLAUDE CODE COMMAND, VERIFIED SKILL INVOCATION, VERIFIED PLUGIN COMMAND, TERMINAL COMMAND, RECOMMENDED NATURAL-LANGUAGE PROMPT, or EXAMPLE — VERIFY BEFORE USE.
4. **Execute in order** — Follow the Execution Order sequence for that phase.
5. **Verify before proceeding** — Check the Verification section before moving to the next phase.
6. **Mark complete** — When Completion Criteria are met, move to the next phase.

## Categories Used Throughout

Every command/prompt is labeled with one of these categories:

| Label | Meaning |
|-------|---------|
| **VERIFIED CLAUDE CODE COMMAND** | Built into the `claude` CLI or Claude Code itself (e.g., `claude doctor`, `claude mcp`, `claude agents`) |
| **VERIFIED SKILL INVOCATION** | Invoked via the Skill tool with an exact `skill` name |
| **VERIFIED PLUGIN COMMAND** | A command provided by an installed plugin |
| **TERMINAL COMMAND** | Ordinary shell/git/build command run in the terminal |
| **RECOMMENDED NATURAL-LANGUAGE PROMPT** | A prompt you type to Claude Code to perform a task |
| **EXAMPLE — VERIFY BEFORE USE** | Example syntax that needs confirmation against your project's tooling |

## Safety Rules

- Inspect before editing.
- Clarify important missing requirements.
- Plan complex tasks before implementation.
- Prefer small, verifiable changes.
- Preserve unrelated existing behavior.
- Run appropriate tests after changes.
- Review diffs before committing.
- Never invent available tools or commands.
- Never expose secrets.
- Never execute destructive operations without explaining consequences.
- Never install or modify plugins as part of this task.
- Never claim tests passed unless they were actually run.
