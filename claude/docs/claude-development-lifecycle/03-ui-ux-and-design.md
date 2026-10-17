# Phase 3: UI/UX and Design

## A. Purpose

Plan the user experience, establish design requirements, create design systems, plan pages and components, and verify accessibility and usability. This phase ensures the application's interface is production-quality, accessible, and consistent.

Use this phase when:
- Building new UI components or pages
- Designing user-facing interfaces for web or mobile applications
- Establishing or updating a design system
- Improving accessibility or usability of existing interfaces
- Creating wireframes, mockups, or design specifications

## B. Required Inputs

- Requirements and specifications from Phase 2
- Understanding of target users and their goals
- Information about target devices and breakpoints
- Access to any existing design system or brand guidelines
- Figma access or design tool access (if available)

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `frontend-ui-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/frontend-ui-engineering/SKILL.md` | Core skill for building production-quality, accessible, responsive UIs |
| `ui-ux-pro-max` (suite) | `/c/Users/sheha/.claude/plugins/cache/ui-ux-pro-max-skill/ui-ux-pro-max/2.13.0/` | UI/UX design support including banner, brand, design, design-system, slides, ui-styling |
| `awesome-design@awesome-design-skill` | `/c/Users/sheha/.claude/plugins/cache/awesome-design-skill/awesome-design/1.0.0/` | Design tokens for 74 well-known brands/products |

### ui-ux-pro-max sub-skills:
- `banner-design` - Banner design
- `brand` - Branding
- `design` - General design
- `design-system` - Design system creation
- `slides` - Presentations
- `ui-styling` - UI styling
- `ui-ux-pro-max` - Core UI/UX skill

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "frontend-ui-engineering" })` - Build production-quality accessible responsive UIs
- `Skill({ skill: "ui-ux-pro-max" })` - UI/UX design support
- `Skill({ skill: "awesome-design" })` - Access design tokens for brand matching

### VERIFIED PLUGIN COMMANDS
None - ui-ux-pro-max and awesome-design skills are invoked through the Skill tool, not dedicated slash commands

### TERMINAL COMMANDS
- `mkdir -p docs/design` - Create design documentation directory
- `mkdir -p src/components` - Create components directory
- `mkdir -p src/styles` - Create styles directory

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Help me plan the user experience for this feature."
- "What design requirements should we establish?"
- "Create a design system for this project."
- "Plan the pages and components needed for this feature."
- "Define responsive behavior at breakpoints 320px, 768px, 1024px, 1440px."
- "Design loading, empty, error, and success states."
- "Review this component for accessibility compliance (WCAG 2.1 AA)."
- "Check keyboard navigation and focus management."
- "Verify color contrast meets 4.5:1 minimum ratio."
- "Create wireframes or mockups for [specific page/component]."

## E. Execution Order

1. **First**: Review requirements and specifications from Phase 2
2. **Second**: Run `Skill({ skill: "frontend-ui-engineering" })` to establish UI design approach
3. **Third**: If matching an existing brand, run `Skill({ skill: "awesome-design" })` to get design tokens
4. **Fourth**: For comprehensive UI/UX support, run `Skill({ skill: "ui-ux-pro-max" })`
5. **Fifth**: Plan pages and components - create component inventory
6. **Sixth**: Define responsive behavior and breakpoints
7. **Seventh**: Design loading, empty, error, and success states
8. **Eighth**: Check accessibility - keyboard navigation, ARIA labels, color contrast
9. **Ninth**: Document design decisions and component specifications

## F. Expected Output

- Design system documentation (colors, typography, spacing, components)
- Component inventory with file locations
- Wireframes or mockups for key pages
- Responsive behavior specification at breakpoints
- State handling documentation (loading, empty, error, success)
- Accessibility checklist and compliance verification
- Component file structure plan

## G. Verification

- [ ] Components follow the project's design system (spacing, colors, typography)
- [ ] All interactive elements are keyboard accessible (Tab through the page)
- [ ] Screen reader can convey page content and structure
- [ ] Responsive design works at 320px, 768px, 1024px, 1440px
- [ ] Loading, empty, error, success states are handled
- [ ] Color is not the sole indicator of state
- [ ] Color contrast meets WCAG 2.1 AA (4.5:1 for normal text)
- [ ] No accessibility warnings in dev tools or axe-core
- [ ] Components are colocated with their tests and types
- [ ] Design decisions are documented

## H. Completion Criteria

You have completed Phase 3 when:
1. Design system or design requirements are documented
2. All pages and components are planned with file locations
3. Responsive behavior is defined for all breakpoints
4. All UI states (loading, empty, error, success) are planned
5. Accessibility requirements are verified (WCAG 2.1 AA)
6. Component architecture follows project conventions
7. Stakeholders have reviewed and approved the design

## I. Common Mistakes

- Building UI without first establishing design requirements
- Using generic "AI aesthetic" (purple gradients, rounded-2xl everywhere, stock layouts)
- Skipping accessibility verification until after implementation
- Not defining loading, empty, and error states
- Using inline styles or arbitrary pixel values instead of design system tokens
- Skipping keyboard navigation testing
- Relying on color alone to convey information
- Not colocating component files (component, test, types, styles)
- Making components too large (over 200 lines) without splitting
