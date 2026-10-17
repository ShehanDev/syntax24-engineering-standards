# Phase 12: Session Handoff

## A. Purpose

Save progress, record files changed, capture tests and failures, record decisions, prepare the next task, and enable continuing work in a new Claude Code session. This phase ensures work can resume seamlessly after interruption or session end.

Use this phase when:
- Pausing work to continue later in a new session
- Switching between different features or tasks
- Taking a break during long development work
- Handing off work to another developer or agent
- Before ending a Claude Code session

## B. Required Inputs

- Current working tree state
- Task progress and next steps
- Test results and any failures
- Decisions made during the session
- Files to review before handoff

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Ensures rules and context are preserved |
| `documenting-and-adrs` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/documenting-and-adrs/SKILL.md` | Documents decisions made in the session |
| `git-workflow-and-versioning` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/git-workflow-and-versioning/SKILL.md` | Records the commit and branch state |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "context-engineering" })` - Ensure context is preserved
- `Skill({ skill: "documenting-and-adrs" })` - Document key decisions
- `Skill({ skill: "git-workflow-and-versioning" })` - Record git state

### TERMINAL COMMANDS
- `git status` — Check current branch and changes
- `git diff` — Show unstaged changes
- `git diff --cached` — Show staged changes
- `git log --oneline -5` — Recent commits
- `git branch` — Current branch

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Save progress and prepare for handoff to a new session."
- "Record what files were changed and what tests ran."
- "Document the decisions made in this session."
- "Create a handoff note for the next task."
- "What should the next session know about this work?"
- "Record any pending tests or failures."
- "Save the remaining task list for continuation."

## E. Execution Order

1. **First**: Record what was accomplished in this session
2. **Second**: Run `Skill({ skill: "context-engineering" })` to capture rules and conventions
3. **Third**: Run `Skill({ skill: "documenting-and-adrs" })` to document decisions
4. **Fourth**: Record files changed and their impact
5. **Fifth**: Record test results and any failures
6. **Sixth**: Run `Skill({ skill: "git-workflow-and-versioning" })` to record commit state
7. **Seventh**: Create handoff note for next task
8. **Eighth**: Update task list with progress

## F. Expected Output

- Handoff note (typically `docs/SESSION-HANDOFF.md` or in `tasks/handoff.md`)
- Updated task list with progress
- Committed changes or documentation of pending work
- List of test results and failures
- Documentation of decisions made

## G. Verification

- [ ] All changes committed or documented as pending
- [ ] Test results recorded (pass/fail counts)
- [ ] Decisions documented with rationale
- [ ] Files changed are tracked
- [ ] Next task is clearly defined
- [ ] Context rules preserved in CLAUDE.md if needed

## H. Completion Criteria

You have completed Phase 12 when:
1. Progress is saved and documented
2. Files changed are recorded
3. Test results are captured
4. Decisions are documented
5. Handoff note is created
6. Next task is ready for the next session

## I. Session Handoff Template

Use this template to create a handoff note at `docs/SESSION-HANDOFF.md`:

```markdown
# Session Handoff - [Date/Time]

## Session Summary
- **Duration**: [X hours]
- **What worked**: [Brief summary of completed work]
- **Challenges**: [Any issues encountered]

## Files Changed
| File | Change Type | Description |
|------|-------------|-------------|
| src/... | Modified | [Description] |
| tests/... | Added | Added test for ... |

## Test Results
- **Unit tests**: [PASSED/FAILED] [N tests passed, M failed]
- **Integration tests**: [PASSED/FAILED]
- **E2E tests**: [PASSED/FAILED]
- **Build**: [PASSED/FAILED]
- **Lint**: [PASSED/FAILED]

## Decisions Made
| Decision | Rationale | Alternatives Considered |
|----------|-----------|------------------------|
| [Decision 1] | [Why this approach] | [Other options] |

## Pending Work
- [ ] [Task description]
- [ ] [Task description]

## Next Task
**Goal**: [What to accomplish next]
**Files likely touched**: [List of files]
**Prerequisite**: [What must be done first]
**Acceptance criteria**: [What defines done for this task]

## Context for Next Session
- [Key context about project state]
- [Important constraints or considerations]
- [Any open questions that need answers]

---
**Session ID**: [session ID for continuation]
**Timestamp**: [ISO timestamp]
```

## Reusable Handoff Checklist

Before ending any session:

- [ ] Git status is clean or changes are documented
- [ ] Tests pass at least for the changed code
- [ ] Build succeeds
- [ ] Decisions are documented
- [ ] Next task is clearly defined
- [ ] Handoff note is created/updated
- [ ] Task list reflects current progress
- [ ] CLAUDE.md has any needed context updates