# Phase 9: Security and Performance

## A. Purpose

Review authentication and authorization, check input validation, detect insecure data handling, review secrets and environment variables, check database queries, investigate performance bottlenecks, and identify unsafe dependencies.

Use this phase when:
- Implementing authentication or authorization
- Storing or transmitting sensitive data
- Integrating with external APIs or services
- Handling user input or file uploads
- Adding payment or PII data handling
- Investigating performance regressions
- Building features that handle large datasets or high traffic
- Before shipping to production

## B. Required Inputs

- Implemented code from Phase 6
- Test results showing behavior
- Specification including security/quality requirements
- Dependencies list (package.json, pom.xml, etc.)
- Environment configuration (.env.example)

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `security-and-hardening` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/security-and-hardening/SKILL.md` | Core security review and hardening |
| `performance-optimization` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/performance-optimization/SKILL.md` | Performance review and optimization |
| `code-review-and-quality` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/code-review-and-quality/SKILL.md` | Includes security and performance axes |
| `browser-testing-with-devtools` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/browser-testing-with-devtools/SKILL.md` | Browser security and performance inspection |
| `observability-and-instrumentation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/observability-and-instrumentation/SKILL.md` | Monitoring setup for security/performance |
| `shipping-and-launch` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/shipping-and-launch/SKILL.md` | Pre-launch security/performance checks |
| `ci-cd-and-automation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/ci-cd-and-automation/SKILL.md` | Dependency audit in CI |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "security-and-hardening" })` - Security review and threat modeling
- `Skill({ skill: "performance-optimization" })` - Performance profiling and optimization
- `Skill({ skill: "observability-and-instrumentation" })` - Monitoring setup

### TERMINAL COMMANDS (Verify against project's package manager)
- `npm audit` — Check Node.js dependencies for vulnerabilities
- `npm audit --audit-level=high` — Check for high+ vulnerabilities only
- `mvn dependency-check:check` — Check Java dependencies (if OWASP plugin configured)
- `pip-audit` — Check Python dependencies
- `cargo audit` — Check Rust dependencies

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Review this code for OWASP Top Ten vulnerabilities."
- "Check authentication and authorization on this endpoint."
- "Is user input validated at the boundary?"
- "Are secrets exposed in code or environment variables?"
- "Check database queries for SQL injection risk."
- "Are API responses encoding output to prevent XSS?"
- "Investigate this performance bottleneck."
- "Check for N+1 query patterns."
- "Are there missing indexes on database queries?"
- "Is caching configured correctly?"
- "Run the dependency audit and triage findings."

## E. Execution Order

1. **First**: Run `Skill({ skill: "security-and-hardening" })` for threat modeling
2. **Second**: Run `Skill({ skill: "performance-optimization" })` for performance review
3. **Third**: Run the ecosystem's dependency audit (`npm audit`, etc.)
4. **Fourth**: Use natural language prompts to check specific concerns (auth, input validation, secrets)
5. **Fifth**: If browser-based, use `Skill({ skill: "browser-testing-with-devtools" })` to check
6. **Sixth**: Run `Skill({ skill: "observability-and-instrumentation" })` to plan monitoring
7. **Seventh**: Address findings with fixes and regression tests
8. **Eighth**: Re-run audits to verify remediation

## F. Expected Output

- Threat model document (trust boundaries, assets, STRIDE analysis)
- Security review report with findings categorized
- Dependency audit results with prioritized remediation
- Performance baseline and optimization recommendations
- Monitoring/observability plan
- Fixes for any critical security issues
- Performance improvements with before/after measurements

## G. Verification

- [ ] The native audit has no unmitigated reachable critical/high findings
- [ ] No secrets in source code or git history
- [ ] All external input validated at system boundaries
- [ ] Authentication and authorization checked on every protected endpoint
- [ ] Security headers present in response
- [ ] Error responses don't expose internal details
- [ ] Rate limiting active on auth endpoints
- [ ] No SQL injection vulnerabilities
- [ ] No XSS vulnerabilities
- [ ] External data sources treated as untrusted
- [ ] Performance has before/after measurements
- [ ] No N+1 query patterns
- [ ] Cache keys include all relevant inputs
- [ ] Monitoring/observability covers key metrics

## H. Completion Criteria

You have completed Phase 9 when:
1. Threat model is documented with STRIDE analysis
2. All critical/high security issues are addressed
3. Dependency audit is clean or remediated
4. Performance bottlenecks identified and fixed
5. Monitoring/observability is in place
6. No OWASP Top Ten vulnerabilities remain
7. Secrets are properly managed
8. All user input is validated at boundaries

## I. Common Mistakes

- Claiming AI review guarantees security (it doesn't — it supplements)
- "This is an internal tool, security doesn't matter"
- "We'll add security later" (security debt is expensive)
- Using `eval()` or `innerHTML` with user-provided data
- Treating client-side validation as security boundary
- Not parameterizing database queries
- Storing secrets in code or environment files
- Not validating external API responses
- Caching the same data with different keys incorrectly
- Optimizing without measuring first
- Keeping optimizations that don't beat the baseline
- Bundling multiple optimizations into one measurement