# Phase 7: Testing and Quality Assurance

## A. Purpose

Write and run unit, integration, and end-to-end tests. Ensure code quality through test-driven development and regression checks. This phase proves code works before it ships.

Use this phase when:
- Implementing any new logic or behavior
- Fixing any bug (the Prove-It Pattern)
- Modifying existing functionality
- Adding edge case handling
- Running existing test suites
- Diagnosing test failures
- Performing regression checks

## B. Required Inputs

- Implemented code from Phase 6
- Approved task with acceptance criteria
- Existing test infrastructure and conventions
- Knowledge of the testing framework in use

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `test-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/test-driven-development/SKILL.md` | Core TDD skill — write tests before code |
| `browser-testing-with-devtools` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/browser-testing-with-devtools/SKILL.md` | Browser-based testing via Chrome DevTools MCP |
| `code-review-and-quality` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/code-review-and-quality/SKILL.md` | Quality assurance through code review |
| `debugging-and-error-recovery` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/debugging-and-error-recovery/SKILL.md` | Diagnose test failures |
| `ci-cd-and-automation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/ci-cd-and-automation/SKILL.md` | CI pipeline testing (E2E, integration) |
| `incremental-implementation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/incremental-implementation/SKILL.md` | Per-increment verification |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "test-driven-development" })` - Core TDD workflow (RED → GREEN → REFACTOR)
- `Skill({ skill: "browser-testing-with-devtools" })` - Browser testing with Chrome DevTools MCP
- `Skill({ skill: "debugging-and-error-recovery" })` - Diagnose failing tests

### TERMINAL COMMANDS (Verify against project's package.json/build files)
- `npm test` — Run test suite (JavaScript/TypeScript)
- `npm test -- --coverage` — Run tests with coverage
- `npm test -- --grep "test name"` — Run a specific focused test
- `./gradlew test` — Run tests in Gradle/Java projects
- `./mvnw test` — Run tests in Maven projects
- `pytest` — Run Python tests
- `go test ./...` — Run Go tests
- `flutter test` — Run Flutter tests
- `npm run lint` — Run linter
- `npx tsc --noEmit` — Type checking (TypeScript)
- `npx playwright test` — Run E2E tests
- `npx jest --watch` — Run tests in watch mode (development)

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Write a failing test that reproduces this bug."
- "Follow the TDD cycle: RED → GREEN → REFACTOR."
- "Run the repository's test command and verify it passes."
- "Test this API endpoint for input validation."
- "Write integration tests for [component/endpoint]."
- "Run tests for just this file."
- "Check if there are any console errors in the browser."
- "Verify network requests are returning expected responses."
- "Check the accessibility tree for this component."

## E. Execution Order

1. **First**: Read the task acceptance criteria and any existing tests
2. **Second**: Discover the project's test framework and commands (`package.json`, `build.gradle`, etc.)
3. **Third**: Run `Skill({ skill: "test-driven-development" })` for the TDD workflow
4. **Fourth**: Write a failing test (RED) for the new behavior
5. **Fifth**: Write minimal code to make the test pass (GREEN)
6. **Sixth**: Clean up the implementation without changing behavior (REFACTOR)
7. **Seventh**: Run the focused test to verify it passes
8. **Eighth**: Run the full test suite to check for regressions
9. **Ninth**: If browser-based, run `Skill({ skill: "browser-testing-with-devtools" })`
10. **Tenth**: Verify build and linting pass

## F. Expected Output

- Failing tests written before implementation (RED)
- Minimal code that makes tests pass (GREEN)
- Refactored code that's cleaner but still passes tests
- Full test suite passing with no regressions
- Test coverage maintained or improved
- For bug fixes: regression test that catches the specific bug
- For UI: console clean, network requests correct, visual state as expected

## G. Verification

- [ ] Every new behavior has a corresponding test
- [ ] The full suite passes, run with the repository's own test command
- [ ] Bug fixes include a reproduction test that failed before the fix
- [ ] Test names describe the behavior being verified
- [ ] No tests were skipped or disabled
- [ ] Coverage hasn't decreased (if tracked)
- [ ] Console has no errors or warnings (browser)
- [ ] Network requests return expected status codes (browser)
- [ ] Accessibility tree shows correct structure (browser)

## H. Completion Criteria

You have completed Phase 7 when:
1. Every new behavior has corresponding tests
2. The full test suite passes
3. Bug fixes include regression tests
4. No tests are skipped or disabled
5. Test names clearly describe expected behavior
6. Build and linting pass
7. Browser-based changes verified in browser (if applicable)

## I. Common Mistakes

- Running a default test command (`npm test`) without checking what this repository actually uses
- Writing tests that pass immediately (they prove nothing)
- Testing implementation details instead of behavior
- Over-mocking dependencies (tests pass but production breaks)
- Not writing regression tests for bug fixes
- Skipping tests because "it's just a prototype"
- Skipping browser testing for UI changes
- Not checking console errors in browser
- Running the same test command twice without code changes