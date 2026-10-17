# Phase 2: Idea Refinement and Requirements

## A. Purpose

Transform vague ideas into concrete, actionable requirements with clear scope, success criteria, and boundaries. This phase ensures everyone agrees on what we're building before investing implementation effort.

Use this phase when:
- Starting with only a rough idea or problem statement
- Requirements are ambiguous, incomplete, or conflicting
- Need to validate assumptions before proceeding
- Defining scope for a new feature or project
- Stakeholders have different interpretations of what's needed

## B. Required Inputs

- Initial idea, problem statement, or feature request
- Access to stakeholders or users who can provide feedback
- Understanding of business context and constraints
- Ability to document decisions (markdown files)

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `idea-refine` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/idea-refine/SKILL.md` | Core skill for refining ideas through structured divergent/convergent thinking |
| `spec-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/spec-driven-development/SKILL.md` | Creates specifications before coding; defines scope and success criteria |
| `doubt-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/doubt-driven-development/SKILL.md` | Questions assumptions and identifies edge cases |
| `interview-me` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/interview-me/SKILL.md` | Structures stakeholder interviews for requirements gathering |
| `documenting-and-adrs` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/documenting-and-adrs/SKILL.md` | Documents decisions and requirements |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "idea-refine" })` - Main entry point for idea refinement process
- `Skill({ skill: "spec-driven-development" })` - Create specifications after ideas are refined
- `Skill({ skill: "doubt-driven-development" })` - Stress-test assumptions and identify risks
- `Skill({ skill: "interview-me" })` - Conduct structured interviews for requirements
- `Skill({ skill: "documenting-and-adrs" })` - Document architectural decisions and requirements

### TERMINAL COMMANDS
- `mkdir -p docs/ideas` - Create directory for idea refinement outputs
- `touch docs/requirements.md` - Create requirements document
- `touch docs/spec.md` - Create specification document

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
For idea-refine skill:
- "Help me refine this idea: [describe your initial idea]"
- "Ideate on [concept]"
- "Stress-test my plan"

For requirements gathering:
- "Who are the primary users of this system and what are their goals?"
- "What does success look like? Define specific, measurable outcomes."
- "What are the functional requirements (what the system must do)?"
- "What are the non-functional requirements (performance, security, usability, etc.)?"
- "What assumptions are we making that need validation?"
- "What is explicitly out of scope for this release/feature?"
- "What edge cases or error conditions should we handle?"
- "What are the acceptance criteria for this feature?"
- "What risks do we anticipate and how might we mitigate them?"

## E. Execution Order

1. **First**: Run `Skill({ skill: "idea-refine" })` with your initial idea as input
2. **Second**: Engage in the interactive dialogue - answer questions, review variations, provide feedback
3. **Third**: When prompted, review the generated idea variations and select directions to explore
4. **Fourth**: Work through the assumption surfacing phase - explicitly name what you're betting is true
5. **Fifth**: Review and confirm the final markdown one-pager output before saving
6. **Sixth**: (Optional) Run `Skill({ skill: "interview-me" })` to conduct stakeholder interviews if needed
7. **Seventh**: Run `Skill({ skill: "doubt-driven-development" })` to stress-test the refined idea
8. **Eighth**: Run `Skill({ skill: "spec-driven-development" })` to create a formal specification
9. **Ninth**: Run `Skill({ skill: "documenting-and-adrs" })` to document key decisions

## F. Expected Output

From idea-refine:
- Markdown one-pager saved to `docs/ideas/[idea-name].md` containing:
  - Problem Statement (HMW format)
  - Recommended Direction
  - Key Assumptions to Validate
  - MVP Scope
  - Not Doing list
  - Open Questions

From spec-driven-development:
- Specification document (typically `SPEC.md` or `SPEC-[feature-name].md`) covering:
  - Objective
  - Tech Stack
  - Commands
  - Project Structure
  - Code Style
  - Testing Strategy
  - Boundaries
  - Success Criteria
  - Open Questions

From documenting-and-adrs:
- Architectural Decision Records in `docs/adr/` directory
- Requirements document at `docs/requirements.md`

## G. Verification

- [ ] Problem statement is written as a clear "How Might We" question
- [ ] Target users and success criteria are explicitly defined
- [ ] Multiple directions were explored, not just the first idea
- [ ] Hidden assumptions are explicitly listed with validation strategies
- [ ] A "Not Doing" list makes trade-offs explicit
- [ ] The output is a concrete artifact (markdown one-pager), not just conversation
- [ ] User confirmed the final direction before any implementation work
- [ ] Specification covers all six core areas (Objective, Tech Stack, Commands, Project Structure, Code Style, Testing Strategy, Boundaries, Success Criteria)
- [ ] Success criteria are specific and testable
- [ ] Boundaries (Always/Ask First/Never) are defined
- [ ] Specification is saved to a file in the repository
- [ ] If multiple capabilities exist, a capability map was approved before any module spec

## H. Completion Criteria

You have completed Phase 2 when:
1. You have a written problem statement in HMW format
2. You can clearly state who the users are and what success looks like
3. You have documented assumptions that need validation
4. You have explicit exclusions (what you're NOT building)
5. You have a specification that covers objective, tech stack, structure, style, testing, boundaries, and success criteria
6. Success criteria are specific, measurable, and testable
7. Stakeholders have reviewed and approved the specification
8. The specification is committed to version control

## I. Common Mistakes

- Skipping the assumption surfacing phase and building on unvalidated beliefs
- Not creating a "Not Doing" list, leading to scope creep
- Writing specifications after coding has begun (documentation vs specification)
- Making success criteria vague or untestable ("make it faster" without metrics)
- Forgetting to define boundaries (what requires approval vs what's always allowed)
- Not getting human approval of the specification before starting implementation
- Creating specifications that bundle multiple independently testable capabilities without a capability map
- Saving specification only in conversation history without committing to files