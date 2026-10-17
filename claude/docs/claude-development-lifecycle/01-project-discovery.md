# Phase 1: Project Discovery and Repository Analysis

## A. Purpose

Understand an existing repository's structure, technology stack, architecture, conventions, and current state before making changes. This phase establishes the baseline for all subsequent work and helps avoid breaking existing patterns.

Use this phase when:
- Starting work on an existing codebase
- Taking over maintenance of a project
- Needing to understand dependencies and constraints
- Planning significant changes or migrations
- Onboarding to a new project

## B. Required Inputs

- Access to the repository (local clone or remote URL)
- Ability to run basic shell commands (ls, grep, find, etc.)
- Read access to configuration files (package.json, pom.xml, Cargo.toml, etc.)
- Repository history (git log) if available

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Helps establish rules files (CLAUDE.md) and context setup for ongoing work |
| `source-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/source-driven-development/SKILL.md` | Verifies technology stack from dependency files against official documentation |
| `git-workflow-and-versioning` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/git-workflow-and-versioning/SKILL.md` | Understands branching strategy, commit conventions, and versioning practices |
| `documenting-and-adrs` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/documenting-and-adrs/SKILL.md` | Discovers existing documentation and architectural decision records |

## D. Commands

### VERIFIED CLAUDE CODE COMMANDS
- `claude doctor` - Check Claude Code installation health
- `claude agents [options]` - Manage background agents (useful for parallel discovery tasks)
- `claude mcp` - Configure and manage MCP servers (for database/schema inspection if configured)

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "source-driven-development" })` - Detect stack from dependency files and fetch official documentation
- `Skill({ skill: "context-engineering" })` - Set up or update CLAUDE.md and rules files
- `Skill({ skill: "git-workflow-and-versioning" })` - Review git workflow and versioning practices
- `Skill({ skill: "documenting-and-adrs" })` - Review existing documentation and ADRs

### TERMINAL COMMANDS
- `git status` - Check current branch and changes
- `git log --oneline -10` - See recent commits
- `git branch -a` - List all branches
- `git remote -v` - Check remote repositories
- `ls -la` - List directory contents (including hidden files)
- `find . -type f -name "package.json" -o -name "pom.xml" -o -name "Cargo.toml" -o -name "go.mod" -o -name "requirements.txt" -o -name "pyproject.toml" -o -name "build.gradle"` - Find dependency/manifest files
- `cat package.json` (or equivalent) - Examine dependencies and scripts
- `ls -la .github/workflows/` - Check CI/CD configuration if present
- `ls -la .claude/` - Check Claude Code project configuration

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "What is the primary technology stack of this project? List all languages, frameworks, and key dependencies with versions."
- "Describe the project's directory structure and naming conventions."
- "What are the main architectural patterns used in this codebase?"
- "Show me the README and any contributing/development documentation."
- "What testing frameworks and strategies are used in this project?"
- "Are there any existing design system or UI component libraries?"
- "What deployment targets or platforms does this project support?"
- "Are there any known issues, technical debt items, or TODOs documented?"

## E. Execution Order

1. **First**: Run `git status` and `git log --oneline -10` to understand current state and recent activity
2. **Second**: Use terminal commands to discover dependency files (`find` commands above)
3. **Third**: Examine each dependency file found (`cat package.json`, `cat pom.xml`, etc.)
4. **Fourth**: Run `Skill({ skill: "source-driven-development" })` to get authoritative versions and patterns
5. **Fifth**: Run `Skill({ skill: "context-engineering" })` to establish/update project rules (CLAUDE.md)
6. **Sixth**: Run `Skill({ skill: "git-workflow-and-versioning" })` to understand branching and release strategies
7. **Seventh**: Run `Skill({ skill: "documenting-and-adrs" })` to review existing documentation
8. **Eighth**: Use natural language prompts to gather additional context about architecture, testing, and deployment

## F. Expected Output

- Current git branch and status
- List of recent commits with messages
- Dependency files identified and examined
- Technology stack with versions (from source-driven-development)
- Updated or created CLAUDE.md with project conventions
- Git workflow documentation (branching strategy, commit conventions)
- Summary of existing documentation and ADRs
- Answers to the natural language prompts about architecture, testing, deployment, etc.

## G. Verification

- [ ] Can correctly state the primary programming language and version
- [ ] Can list 3+ key dependencies with their versions
- [ ] Can describe the directory structure convention (src/tests separation, etc.)
- [ ] Has identified the main entry point(s) of the application
- [ ] Can explain how to run tests and build the project
- [ ] Has reviewed any existing architectural documentation
- [ ] Has confirmed git branching and release strategy

## H. Completion Criteria

You have completed Phase 1 when you can answer these questions without hesitation:
1. What language(s) and framework(s) is this project built with?
2. How do I build, test, and run this project locally?
3. What are the key architectural components and their interactions?
4. What testing strategy is employed?
5. What are the deployment targets/platforms?
6. What git workflow and branching strategy is used?
7. Are there any established coding or UI conventions documented?

## I. Common Mistakes

- Assuming technology stack without checking actual dependency files
- Skipping git history review and missing important context about recent changes
- Not checking for existing documentation before making assumptions
- Overlooking CI/CD configuration that reveals testing and deployment practices
- Forgetting to check for .env.example or configuration templates that reveal required environment variables
- Missing CLI-specific commands in package.json scripts that reveal how to run the project