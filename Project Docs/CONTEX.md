# AI Coding Agent Context Setup

This directory contains the core project context files to ensure the AI coding agent understands the product scope, coding rules, UI decisions, and system architecture before writing any code.

## Quick Rule of Thumb
* **`PRD.md`** = What are we building?
* **`AGENTS.md`** = How should the AI work?
* **`DESIGN_SYSTEM.md`** = How should it look?
* **`ARCHITECTURE.md`** = How should it connect?

## Agent Kickoff Prompt
*Copy and paste this prompt to start a new session with your AI coding agent:*

> Before writing code, read:
> - PRD.md
> - AGENTS.md
> - DESIGN_SYSTEM.md
> - ARCHITECTURE.md
> 
> Use these files as the source of truth for product scope, coding rules, UI decisions, and system architecture.
> 
> Before creating a new component or pattern, check whether one already exists. Do not change the architecture or add new dependencies unless they are necessary.
> 
> If the files conflict or an important decision is missing, ask for clarification before making a major assumption.

## Maintenance Rules
1. Fill the files with specific decisions; avoid vague instructions like "make it modern."
2. Tell the agent which files to read at the beginning of every build.
3. Update the relevant Markdown file when a product decision changes so the context stays current.
4. Keep the files focused on their specific domains.
5. Treat these documents as living context, not one-time setup files.