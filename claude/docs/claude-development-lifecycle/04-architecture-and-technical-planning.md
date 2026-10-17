# Phase 4: Architecture and Technical Planning

## A. Purpose

Select appropriate architecture, understand constraints, design backend/frontend boundaries, plan database schemas, design REST API contracts, identify integrations, document decisions, and plan migrations. This phase creates the technical blueprint before implementation begins.

Use this phase when:
- Starting a new project or significant refactor
- Designing system boundaries and interfaces
- Planning database schema or data models
- Creating API contracts or service interfaces
- Identifying third-party integrations and dependencies
- Making architectural decisions that affect multiple components
- Planning data migrations or schema changes

## B. Required Inputs

- Approved specification from Phase 2
- UI/UX designs and component plans from Phase 3
- Understanding of non-functional requirements (performance, scale, security)
- Knowledge of team skills and organizational constraints
- Budget and timeline considerations

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `api-and-interface-design` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/api-and-interface-design/SKILL.md` | Core skill for designing stable APIs and interfaces |
| `spec-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/spec-driven-development/SKILL.md` | Helps define technical specifications and boundaries |
| `source-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/source-driven-development/SKILL.md` | Verifies approaches against official framework documentation |
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Establishes architectural rules in CLAUDE.md |
| `documenting-and-adrs` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/documenting-and-adrs/SKILL.md` | Documents architectural decisions |
| `deprecation-and-migration` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/deprecation-and-migration/SKILL.md` | Plans safe migrations and deprecations |
| `observability-and-instrumentation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/observability-and-instrumentation/SKILL.md` | Plans monitoring and observability |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "api-and-interface-design" })` - Design APIs, module boundaries, contracts
- `Skill({ skill: "spec-driven-development" })` - Create technical specifications
- `Skill({ skill: "source-driven-development" })` - Verify implementation approaches
- `Skill({ skill: "context-engineering" })` - Set/update architectural rules (CLAUDE.md)
- `Skill({ skill: "documenting-and-adrs" })` - Document architectural decisions (ADRs)
- `Skill({ skill: "deprecation-and-migration" })` - Plan migrations and deprecations
- `Skill({ skill: "observability-and-instrumentation" })` - Plan monitoring strategy

### TERMINAL COMMANDS
- `mkdir -p docs/architecture` - Create architecture documentation
- `mkdir -p docs/api` - Create API documentation
- `mkdir -p docs/adr` - Create Architectural Decision Records directory
- `touch docs/architecture/overview.md` - Create architecture overview
- `touch docs/api/contracts.md` - Create API contracts document

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "What architectural style should we use (monolith, microservices, serverless, etc.)?"
- "How should we split responsibilities between frontend and backend?"
- "What database technology and schema should we use?"
- "Design the REST API contracts for [specific resource]."
- "What third-party services or APIs do we need to integrate with?"
- "What are the key architectural constraints we must work within?"
- "How should we handle authentication and authorization?"
- "What caching strategy should we implement?"
- "How will we handle asynchronous processing or background jobs?"
- "What monitoring and observability do we need?"
- "Are there any planned migrations or breaking changes?"
- "How should we handle configuration and environment variables?"

## E. Execution Order

1. **First**: Review approved specification and UI/UX designs
2. **Second**: Run `Skill({ skill: "api-and-interface-design" })` to design API contracts and interfaces
3. **Third**: Run `Skill({ skill: "source-driven-development" })` to verify architectural approaches against official docs
4. **Fourth**: Run `Skill({ skill: "context-engineering" })` to establish/update architectural rules in CLAUDE.md
5. **Fifth**: Run `Skill({ skill: "documenting-and-adrs" })` to document key architectural decisions
6. **Sixth**: If migrations are needed, run `Skill({ skill: "deprecation-and-migration" })` to plan them
7. **Seventh**: Run `Skill({ skill: "observability-and-instrumentation" })` to plan monitoring strategy
8. **Eighth**: Use natural language prompts to clarify specific architectural decisions
9. **Ninth**: Create architecture overview and API documentation files

## F. Expected Output

- Architecture decision records (ADRs) in `docs/adr/` directory
- API contracts document (typically `docs/api/contracts.md`)
- Database schema design document
- Technology stack and version decisions
- Architectural overview document
- Integration points and third-party service list
- Migration plan (if applicable)
- Monitoring and observability plan
- Updated CLAUDE.md with architectural rules and boundaries

## G. Verification

- [ ] API contracts have typed input and output schemas
- [ ] Error responses follow a consistent format
- [ ] Validation happens at system boundaries only
- [ ] Architectural decisions are documented with context and consequences
- [ ] Database schema is designed for scalability and integrity
- [ ] Authentication and authorization approaches are defined
- [ ] Third-party integrations are identified with contracts
- [ ] Monitoring strategy covers key metrics and error tracking
- [ ] Migration plan includes rollback procedures
- [ ] Architecture aligns with non-functional requirements (performance, security, scale)

## H. Completion Criteria

You have completed Phase 4 when:
1. API contracts and interfaces are designed and documented
2. Database schema and data models are planned
3. Architectural decisions are documented as ADRs
4. Technology stack choices are verified against official documentation
5. Integration points with third-party services are identified
6. Monitoring and observability strategy is defined
7. Migration plan exists (if schema changes are needed)
8. CLAUDE.md contains architectural rules and boundaries
9. Stakeholders have reviewed and approved the architectural plan

## I. Common Mistakes

- Over-engineering with unnecessary microservices or complexity
- Not validating architectural choices against official framework documentation
- Skipping API contract design and jumping straight to implementation
- Not defining clear boundaries between frontend/backend or modules
- Forgetting to plan for error handling and partial failures
- Overlooking data migration requirements when changing schemas
- Not considering performance implications of architectural choices
- Skipping observability planning until after implementation
- Not documenting why certain architectural decisions were made
- Creating tight coupling between components that should be independent