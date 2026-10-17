# Commands Quick Reference

A consolidated table of all verified commands, skill invocations, and prompts covered in this cookbook.

## Legend

| Label | Meaning |
|-------|---------|
| **CC** | VERIFIED CLAUDE CODE COMMAND — Built into `claude` CLI |
| **SK** | VERIFIED SKILL INVOCATION — Invoked via Skill tool |
| **PL** | VERIFIED PLUGIN COMMAND — From installed plugin |
| **SH** | TERMINAL COMMAND — Shell command run in terminal |
| **NL** | RECOMMENDED NATURAL-LANGUAGE PROMPT — Prompt to Claude Code |
| **EX** | EXAMPLE — VERIFY BEFORE USE — Example syntax, confirm before use |

## Quick Reference Table

| Phase | Command or Prompt | Type | Source | Purpose | Expected Result | Verification |
|-------|-------------------|------|--------|---------|-----------------|-------------|
| All | `Skill({ skill: "context-engineering" })` | SK | agent-skills | Set up rules, CLAUDE.md, context | Rules file | Read CLAUDE.md |
| All | `Skill({ skill: "source-driven-development" })` | SK | agent-skills | Verify code against official docs | Version detection, doc snippets | Versions match deps |
| All | `Skill({ skill: "documenting-and-adrs" })` | SK | agent-skills | Document decisions | ADR files | ADR committed |
| All | `Skill({ skill: "git-workflow-and-versioning" })` | SK | agent-skills | Git workflow setup | Branch/commit conventions | Branch matches plan |
| 1 | `git status` | SH | git | Check working tree | Current branch, changes | Status matches intent |
| 1 | `git log --oneline -10` | SH | git | Recent commits | Commit history | History reviewed |
| 1 | `claude doctor` | CC | Claude Code | Health check | Health report | Report passes |
| 1 | `Skill({ skill: "source-driven-development" })` | SK | agent-skills | Detect stack, fetch docs | Versions, patterns | Versions verified |
| 1 | "What is the primary technology stack?" | NL | — | Discover stack | Stack summary | Stack confirmed |
| 2 | `Skill({ skill: "idea-refine" })` | SK | agent-skills | Refine ideas | Idea one-pager | Assumptions listed |
| 2 | `Skill({ skill: "spec-driven-development" })` | SK | agent-skills | Create specification | SPEC.md | Spec approved |
| 2 | `Skill({ skill: "interview-me" })` | SK | agent-skills | Stakeholder interviews | Interview guide | Questions defined |
| 2 | `Skill({ skill: "doubt-driven-development" })` | SK | agent-skills | Stress-test assumptions | Risk analysis | Risks listed |
| 2 | "Help me refine this idea" | NL | idea-refine | Trigger idea refinement | Idea exploration | Idea documented |
| 3 | `Skill({ skill: "frontend-ui-engineering" })` | SK | agent-skills | Build production UIs | Component code | Components built |
| 3 | `Skill({ skill: "ui-ux-pro-max" })` | SK | ui-ux-pro-max | UI/UX design | Design specs | Designs approved |
| 3 | `Skill({ skill: "awesome-design" })` | SK | awesome-design | Design tokens | Brand tokens | Tokens documented |
| 3 | "Check accessibility compliance" | NL | frontend-ui-engineering | Accessibility review | A11y checklist | Checklist passes |
| 4 | `Skill({ skill: "api-and-interface-design" })` | SK | agent-skills | Design API contracts | API spec | Contracts signed |
| 4 | `Skill({ skill: "deprecation-and-migration" })` | SK | agent-skills | Plan migrations | Migration plan | Plan verified |
| 4 | `Skill({ skill: "observability-and-instrumentation" })` | SK | agent-skills | Monitoring setup | Observability plan | Plan approved |
| 4 | "Design REST API contracts" | NL | api-and-interface-design | API design | API documentation | Endpoints defined |
| 5 | `Skill({ skill: "planning-and-task-breakdown" })` | SK | agent-skills | Break into tasks | tasks/plan.md, todo.md | Tasks reviewed |
| 5 | `Skill({ skill: "incremental-implementation" })` | SK | agent-skills | Incremental guidance | Implementation steps | Steps verified |
| 5 | "Break this spec into small tasks" | NL | planning-and-task-breakdown | Task decomposition | Task list | List complete |
| 6 | `Skill({ skill: "incremental-implementation" })` | SK | agent-skills | Implement slices | Working code | Each slice tested |
| 6 | `Skill({ skill: "frontend-ui-engineering" })` | SK | agent-skills | Frontend implementation | UI components | UI verified |
| 6 | `npm run dev` | SH | project | Start dev server | Running server | Server on port X |
| 6 | `npm run build` | SH | project | Build project | Build artifacts | Build passes |
| 6 | `./gradlew bootRun` | SH | project | Run Spring Boot | Running app | App accessible |
| 6 | `flutter run` | SH | project | Run Flutter app | Running app | App on device |
| 6 | "Implement Task N from the plan" | NL | incremental-implementation | Start task | Implementation | Task complete |
| 7 | `Skill({ skill: "test-driven-development" })` | SK | agent-skills | TDD workflow | Tests + code | Tests passing |
| 7 | `Skill({ skill: "browser-testing-with-devtools" })` | SK | agent-skills | Browser testing | DOM/screenshots | Console clean |
| 7 | `npm test` | SH | project | Run tests | Test results | Suite passes |
| 7 | `./gradlew test` | SH | project | Run Java tests | Test results | Suite passes |
| 7 | `pytest` | SH | project | Run Python tests | Test results | Suite passes |
| 7 | `flutter test` | SH | project | Run Flutter tests | Test results | Suite passes |
| 7 | "Write a failing test that reproduces this bug" | NL | test-driven-development | Bug reproduction | Regression test | Test fails |
| 8 | `Skill({ skill: "code-review-and-quality" })` | SK | agent-skills | Multi-axis review | Review report | Issues addressed |
| 8 | `Skill({ skill: "code-simplification" })` | SK | agent-skills | Simplify code | Refactored code | Same behavior |
| 8 | `git diff` | SH | git | Show changes | Diff output | Diff reviewed |
| 8 | `Skill({ skill: "security-and-hardening" })` | SK | agent-skills | Security review | Security findings | Findings addressed |
| 8 | `Skill({ skill: "performance-optimization" })` | SK | agent-skills | Performance review | Perf findings | Findings addressed |
| 8 | "Review this diff for correctness" | NL | code-review-and-quality | Code review | Review comments | Comments resolved |
| 9 | `Skill({ skill: "security-and-hardening" })` | SK | agent-skills | Security hardening | Security report | No critical issues |
| 9 | `Skill({ skill: "performance-optimization" })` | SK | agent-skills | Performance optimization | Perf report | Improvements made |
| 9 | `Skill({ skill: "observability-and-instrumentation" })` | SK | agent-skills | Monitoring setup | Monitoring plan | Plan approved |
| 9 | `npm audit` | SH | project | Dependency audit | Audit report | No critical vulns |
| 9 | `mvn dependency-check:check` | SH | project | Java dependency audit | Audit report | No critical vulns |
| 9 | "Review for OWASP Top Ten" | NL | security-and-hardening | Security audit | Security findings | Findings addressed |
| 10 | `Skill({ skill: "shipping-and-launch" })` | SK | agent-skills | Pre-launch checklist | Checklist complete | All green |
| 10 | `Skill({ skill: "ci-cd-and-automation" })` | SK | agent-skills | CI/CD config | Pipeline config | Pipeline verified |
| 10 | `npm run build` | SH | project | Production build | Build artifacts | Build passes |
| 10 | `docker build .` | SH | docker | Build Docker image | Image | Image builds |
| 10 | `git tag v1.0.0` | SH | git | Create release tag | Tag | Tag pushed |
| 10 | "Run the pre-launch checklist" | NL | shipping-and-launch | Release prep | Checklist items | All items green |
| 11 | `Skill({ skill: "debugging-and-error-recovery" })` | SK | agent-skills | Systematic debugging | Bug fix | Bug fixed |
| 11 | `Skill({ skill: "test-driven-development" })` | SK | agent-skills | Regression test | Test + fix | Tests pass |
| 11 | `git blame <file>` | SH | git | Find code author | Author/date | Context found |
| 11 | `tail -f logs/app.log` | SH | terminal | Follow logs | Log stream | Error found |
| 11 | "Help me reproduce this bug" | NL | debugging-and-error-recovery | Bug reproduction | Reproduction steps | Bug reproduced |
| 12 | `Skill({ skill: "context-engineering" })` | SK | agent-skills | Preserve context | Context saved | Context updated |
| 12 | `git status` | SH | git | Check state | Status | State recorded |
| 12 | "Save progress for handoff" | NL | context-engineering | Create handoff | Handoff doc | Doc created |

## Built-in Claude Code Commands (Reference)

| Command | Description | When to Use |
|---------|-------------|-------------|
| `claude --help` | Show all available commands | First time usage |
| `claude doctor` | Check installation health | Troubleshooting |
| `claude agents` | Manage background agents | Parallel work |
| `claude mcp` | Configure MCP servers | MCP setup |
| `claude plugin` | Manage plugins | Plugin management |
| `claude update` | Check for updates | Staying current |
| `claude ultrareview` | Cloud multi-agent review | Pre-merge review |
| `claude --print` | Non-interactive mode | Scripting |

## Natural Language Prompt Templates

### Project Discovery
```
"What is the primary technology stack of this project? List all languages, frameworks, and key dependencies with versions."
```

### Idea Refinement
```
"Help me refine this idea: [replace with your idea description]"
```

### Requirements Gathering
```
"Who are the primary users of this system and what are their goals?"
"What does success look like? Define specific, measurable outcomes."
"What assumptions are we making that need validation?"
```

### API Design
```
"Design the REST API contracts for [resource name]. Define input/output schemas, error formats, and pagination."
```

### Code Review
```
"Review this code change for correctness, security, and adherence to project conventions. The spec says [X]. The change should [Y]."
```

### Testing
```
"Write a failing test that reproduces this bug: [bug description]. The test should fail with the current code."
```

### Debugging
```
"I'm following the debugging triage checklist. Help me reproduce, localize, reduce, and fix this issue: [error description]"
```

### Handoff
```
"Save progress and prepare for handoff to a new session. Create a handoff note at docs/SESSION-HANDOFF.md."
```

For copy-paste-ready prompts, replace bracketed text with your specific details.