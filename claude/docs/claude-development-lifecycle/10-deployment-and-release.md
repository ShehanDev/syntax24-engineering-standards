# Phase 10: Deployment and Release

## A. Purpose

Prepare a release, run production build checks, verify environment variables, review database migrations, check deployment configuration, prepare rollback procedures, and investigate failed deployments. This phase ensures safe, observable, reversible releases.

Use this phase when:
- Preparing to deploy to production
- Releasing a significant change to users
- Opening a beta or early access program
- Any deployment that carries risk
- Planning a staged rollout or feature flag strategy
- Investigating failed deployments

## B. Required Inputs

- All implemented and tested code
- Passed test suite and code review
- Approved specification and architecture
- Build artifacts ready for deployment
- Environment-specific configuration
- Monitoring and observability setup

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `shipping-and-launch` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/shipping-and-launch/SKILL.md` | Core pre-launch checklist and rollout strategy |
| `ci-cd-and-automation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/ci-cd-and-automation/SKILL.md` | CI/CD pipeline and deployment automation |
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Ensures deployment conventions understood |
| `documenting-and-adrs` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/documenting-and-adrs/SKILL.md` | Documents deployment decisions |
| `observability-and-instrumentation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/observability-and-instrumentation/SKILL.md` | Sets up monitoring for release |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "shipping-and-launch" })` - Pre-launch checklist, rollout strategy, rollback plan
- `Skill({ skill: "ci-cd-and-automation" })` - CI/CD pipeline configuration and deployment strategies
- `Skill({ skill: "observability-and-instrumentation" })` - Monitoring and observability setup

### TERMINAL COMMANDS (Verify against project's CI/CD config)
- `npm run build` — Create production build
- `npm run start:prod` or similar — Start production server
- `docker build .` — Build Docker image (if containerized)
- `docker run <image>` — Run container locally
- `kubectl apply -f deployment.yaml` — Deploy to Kubernetes
- `vercel` or `netlify deploy` — Deploy to Vercel/Netlify
- `aws s3 sync` or `aws deploy` — Deploy to AWS
- `git tag vX.Y.Z` — Create release tag
- `git push --tags` — Push tags to remote

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Run the pre-launch checklist for this release."
- "Verify all environment variables are set correctly."
- "Check that database migrations are ready to apply."
- "Review the deployment configuration for correctness."
- "Prepare a rollback procedure for this release."
- "Set up monitoring for the first hour after launch."
- "What feature flags should be used for this release?"
- "How will we monitor error rates and latency after deployment?"
- "What is our rollback trigger criteria?"
- "Are there any breaking changes that require migration scripts?"

## E. Execution Order

1. **First**: Run `Skill({ skill: "shipping-and-launch" })` for pre-launch checklist
2. **Second**: Run `Skill({ skill: "ci-cd-and-automation" })` to verify/deploy CI/CD pipeline
3. **Third**: Run production build (`npm run build` or equivalent)
4. **Fourth**: Verify environment variables match `.env.example` or deployment platform
5. **Fifth**: Check database migrations are ready and tested
6. **Sixth**: Review deployment configuration (Dockerfile, k8s manifests, Vercel settings, etc.)
7. **Seventh**: Prepare rollback procedure and test it
8. **Eighth**: Run `Skill({ skill: "observability-and-instrumentation" })` to set up monitoring
9. **Ninth**: Create feature flag strategy if needed
10. **Tenth**: Document release notes and version

## F. Expected Output

- Production build artifacts created and verified
- Environment variables validated and set
- Database migration scripts ready and tested
- Deployment configuration reviewed and approved
- Rollback procedure documented and tested
- Monitoring dashboards and alerts configured
- Feature flags created for gradual rollout
- Release notes documenting changes
- Version tag created and pushed

## G. Verification

- [ ] Pre-launch checklist completed (all sections green)
- [ ] Build succeeds with no warnings
- [ ] Lint and type checking pass
- [ ] Code reviewed and approved
- [ ] No secrets in code or version control
- [ ] Ecosystem's dependency audit shows no critical/high vulnerabilities
- [ ] Input validation on all user-facing endpoints
- [ ] Authentication and authorization checks in place
- [ ] Security headers configured
- [ ] Rate limiting on authentication endpoints
- [ ] CORS configured to specific origins
- [ ] Core Web Vitals within "Good" thresholds
- [ ] Images optimized
- [ ] Bundle size within budget
- [ ] Database queries have appropriate indexes
- [ ] Caching configured for static assets/repeated queries
- [ ] Keyboard navigation works for all interactive elements
- [ ] Screen reader can convey page content and structure
- [ ] Color contrast meets WCAG 2.1 AA
- [ ] Focus management correct for modals/dynamic content
- [ ] Error messages descriptive and associated with form fields
- [ ] No accessibility warnings in axe-core or Lighthouse
- [ ] Environment variables set in production
- [ ] Database migrations applied or ready to apply
- [ ] DNS and SSL configured
- [ ] CDN configured for static assets
- [ ] Logging and error reporting configured
- [ ] Health check endpoint exists and responds
- [ ] README updated with setup requirements
- [ ] API documentation current
- [ ] ADRs written for architectural decisions
- [ ] Changelog updated
- [ ] User-facing documentation updated

## H. Completion Criteria

You have completed Phase 10 when:
1. Pre-launch checklist is fully completed and green
2. Production build is verified and ready
3. Environment variables are correctly set
4. Database migrations are prepared and tested
5. Deployment configuration is reviewed and approved
6. Rollback procedure is documented and verified
7. Monitoring and observability are in place
8. Release notes and documentation are updated
9. Version is tagged and ready for deployment

## I. Common Mistakes

- Deploying without a rollback plan
- No monitoring or error reporting in production
- Big-bang releases (everything at once, no staging)
- Feature flags with no expiration or owner
- No one monitoring the deploy for the first hour
- Production environment configuration done by memory, not code
- "It's Friday afternoon, let's ship it"
- Error budget exhausted but feature work continues unchanged
- Shipping UI changes without viewing them in a browser
- Console errors ignored as "known issues"
- Network failures not investigated
- Performance never measured, only assumed
- Accessibility tree never inspected