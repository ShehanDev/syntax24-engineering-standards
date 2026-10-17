# Phase 8: Code Review and Refactoring

## A. Purpose

Review diffs, identify logic errors, check maintainability, detect duplication, verify error handling, review performance, refactor safely, and avoid scope creep. Every change is reviewed before merge.

Use this phase when:
- Reviewing a diff or pull request
- After completing a feature implementation
- When code was written by another agent or human
- When refactoring existing code
- After any bug fix (review both fix and regression test)

## B. Required Inputs

- Changes to review (diff, PR, or file changes)
- Specification and acceptance criteria the change implements
- Test results and build output
- Project conventions and coding standards

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `code-review-and-quality` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/code-review-and-quality/SKILL.md` | Core skill for multi-axis code review |
| `code-simplification` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/code-simplification/SKILL.md` | Refactoring for clarity without behavior change |
| `security-and-hardening` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/security-and-hardening/SKILL.md` | Security-focused review |
| `performance-optimization` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/performance-optimization/SKILL.md` | Performance-focused review |
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Ensures conventions are understood |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "code-review-and-quality" })` - Multi-axis review (correctness, readability, architecture, security, performance)
- `Skill({ skill: "code-simplification" })` - Simplify code for clarity
- `Skill({ skill: "security-and-hardening" })` - Security-focused review

### TERMINAL COMMANDS
- `git diff` — Show unstaged changes
- `git diff --cached` — Show staged changes
- `git diff <branch1> <branch2>` — Compare branches
- `git log --oneline -10` — Recent commits
- `npm run lint --fix` — Auto-fix lint issues
- `npx tsc --noEmit` — Type checking

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Review this diff for correctness, security, and adherence to project conventions."
- "Identify any logic errors in this change."
- "Check for duplicated code that should be shared."
- "Review error handling — are all edge cases covered?"
- "Refactor this code for clarity without changing behavior."
- "Identify any performance concerns in this change."
- "Does this change stay within the requested scope?"

## E. Execution Order

1. **First**: Understand context — what is this change trying to accomplish? What spec/task does it implement?
2. **Second**: Review tests first — do tests exist? Do they test behavior? Are edge cases covered?
3. **Third**: Run `Skill({ skill: "code-review-and-quality" })` for five-axis review
4. **Fourth**: Review implementation across correctness, readability, architecture, security, performance
5. **Fifth**: Categorize findings by severity (Critical/Required/Nit/Optional/FYI)
6. **Sixth**: Verify the verification — what tests were run? Did build pass?
7. **Seventh**: If refactoring needed, run `Skill({ skill: "code-simplification" })`
8. **Eighth**: Require agent to explain significant findings and verify fixes

## F. Expected Output

- Review findings categorized by severity
- Approved change or requested changes list
- Simplified/refactored code (if applicable)
- Updated CLAUDE.md conventions (if new patterns discovered)
- Verification story documented (what was tested, how)

## G. Verification

- [ ] All Critical issues resolved
- [ ] All Required changes resolved or explicitly deferred with justification
- [ ] Tests pass
- [ ] Build succeeds
- [ ] Verification story is documented
- [ ] No scope creep — changes stay within requested scope
- [ ] Agent explained significant findings
- [ ] Fixes verified before proceeding

## H. Completion Criteria

You have completed Phase 8 when:
1. All Critical issues are resolved
2. All Required changes are addressed
3. Tests pass and build succeeds
4. The change improves overall code health
5. No scope creep detected
6. Verification story documented
7. Stakeholder or reviewer has approved

## I. Common Mistakes

- Rubber-stamping ("LGTM" without evidence of review)
- Softening real issues to avoid conflict
- Accepting "I'll clean it up later"
- Reviewing only if tests pass (ignoring other axes)
- Merging without any review
- Security-sensitive changes without security-focused review
- Large PRs that are "too big to review properly"
- Review comments without severity labels
- Not requiring the agent to explain findings and verify fixes