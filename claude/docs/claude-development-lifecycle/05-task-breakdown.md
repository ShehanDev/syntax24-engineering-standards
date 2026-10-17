# Phase 5: Task Breakdown and Implementation Planning

## A. Purpose

Break specifications into small, ordered, verifiable tasks with explicit acceptance criteria. This phase transforms a plan into actionable implementation steps that can be executed incrementally.

Use this phase when:
- You have a spec or clear requirements and need to break work into implementable tasks
- A task feels too large or vague to start
- Work needs to be parallelized across multiple agents or sessions
- You need to communicate scope to a human
- The implementation order isn't obvious

## B. Required Inputs

- Approved specification from Phase 2
- Architecture and technical plan from Phase 4
- UI/UX designs and component plans from Phase 3
- Understanding of dependencies and constraints

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `planning-and-task-breakdown` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/planning-and-task-breakdown/SKILL.md` | Core skill for breaking work into ordered tasks |
| `spec-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/spec-driven-development/SKILL.md` | Provides the specification to break down |
| `incremental-implementation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/incremental-implementation/SKILL.md` | Guides incremental implementation after task breakdown |
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Ensures context is available for each task |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "planning-and-task-breakdown" })` - Break work into ordered tasks
- `Skill({ skill: "spec-driven-development" })` - Review specification for task breakdown
- `Skill({ skill: "incremental-implementation" })` - Guide incremental implementation after breakdown

### TERMINAL COMMANDS
- `mkdir -p tasks` - Create tasks directory
- `touch tasks/plan.md` - Create implementation plan document
- `touch tasks/todo.md` - Create task list

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Break this specification into small, implementable tasks."
- "What is the dependency graph for this feature?"
- "What should be built first, second, third?"
- "Which tasks can be built in parallel?"
- "What are the risks and mitigation strategies?"
- "What verification checkpoints should we establish?"
- "If requirements are incomplete, what assumptions should we make?"

## E. Execution Order

1. **First**: Review approved specification and architecture plan
2. **Second**: Run `Skill({ skill: "planning-and-task-breakdown" })` to create task breakdown
3. **Third**: Review the generated plan document and task list
4. **Fourth**: Identify dependencies and order tasks correctly
5. **Fifth**: Establish checkpoints between major phases
6. **Sixth**: Run `Skill({ skill: "incremental-implementation" })` to guide implementation approach
7. **Seventh**: Review the plan with stakeholders before implementation

## F. Expected Output

- Implementation plan document at `tasks/plan.md` containing:
  - Overview
  - Architecture Decisions
  - Task List (with phases)
  - Checkpoints
  - Risks and Mitigations
  - Open Questions
- Task list at `tasks/todo.md` with:
  - Each task: description, acceptance criteria, verification steps, dependencies, files likely touched, estimated scope
  - Checkpoints between phases

## G. Verification

- [ ] Every task has acceptance criteria
- [ ] Every task has a verification step
- [ ] Task dependencies are identified and ordered correctly
- [ ] Tasks are recorded in the task list target (default `tasks/todo.md`)
- [ ] No pre-existing incomplete plan was overwritten without explicit user confirmation
- [ ] No task touches more than ~5 files
- [ ] Checkpoints exist between major phases
- [ ] The human has reviewed and approved the plan

## H. Completion Criteria

You have completed Phase 5 when:
1. Every task has explicit acceptance criteria
2. Every task has a verification step (test command, build, manual check)
3. Task dependencies are identified and ordered correctly
4. Tasks are recorded in the task list target
5. No pre-existing incomplete plan was overwritten
6. No task touches more than ~5 files
7. Checkpoints exist between major phases
8. The human has reviewed and approved the plan

## I. Common Mistakes

- Starting implementation without a written task list
- Overwriting a `tasks/plan.md` or `tasks/todo.md` that still has unchecked tasks for different work, without asking
- Writing `tasks/todo.md` when the project has designated an external tracker
- Tasks that say "implement the feature" without acceptance criteria
- No verification steps in the plan
- All tasks are XL-sized
- No checkpoints between tasks
- Dependency order isn't considered
- Breaking tasks too large to complete in one session
- Not considering parallelization opportunities