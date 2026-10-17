# Phase 6: Implementation

## A. Purpose

Implement features one at a time following project instructions, reusing existing patterns, and avoiding unrelated refactoring. This phase turns the task breakdown into working code.

Use this phase when:
- Implementing one feature at a time from the task breakdown
- Building frontend components, backend services, API endpoints
- Integrating databases and third-party services
- Writing Java/Spring Boot, React/Next.js, TypeScript, SQL, or Flutter code
- Reviewing changes after each task

## B. Required Inputs

- Approved task breakdown from Phase 5
- Specification with tech stack and commands
- Architecture plan and API contracts
- Design system and component specifications
- Working development environment

## C. Skills and Plugins

| Skill/Plugin | Source Path | Relevance |
|--------------|-------------|-----------|
| `incremental-implementation` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/incremental-implementation/SKILL.md` | Core skill for building in thin, verifiable slices |
| `spec-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/spec-driven-development/SKILL.md` | Provides spec guidance for implementation |
| `source-driven-development` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/source-driven-development/SKILL.md` | Verifies framework-specific code against official docs |
| `frontend-ui-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/frontend-ui-engineering/SKILL.md` | Guides frontend component implementation |
| `api-and-interface-design` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/api-and-interface-design/SKILL.md` | Guides API endpoint implementation |
| `context-engineering` | `/c/Users/sheha/.claude/plugins/cache/addy-agent-skills/agent-skills/0.6.12/skills/context-engineering/SKILL.md` | Ensures proper context for each task |

## D. Commands

### VERIFIED SKILL INVOCATIONS
- `Skill({ skill: "incremental-implementation" })` - Implement in thin, verifiable slices
- `Skill({ skill: "source-driven-development" })` - Verify code against official framework docs
- `Skill({ skill: "frontend-ui-engineering" })` - Implement frontend components
- `Skill({ skill: "api-and-interface-design" })` - Implement API interfaces
- `Skill({ skill: "spec-driven-development" })` - Follow spec during implementation

### TERMINAL COMMANDS (Project-dependent — verify from package.json/pom.xml/build.gradle)
- `npm run dev` — Start development server (Node.js/Next.js/React)
- `npm run build` — Build project for production
- `mvn spring-boot:run` or `./mvnw spring-boot:run` — Run Spring Boot backend
- `./gradlew bootRun` — Run Spring Boot with Gradle
- `flutter run` — Run Flutter application
- `npm install` — Install Node.js dependencies
- `git add <file> && git commit -m "message"` — Commit changes

### RECOMMENDED NATURAL-LANGUAGE PROMPTS
- "Implement Task [N] from the plan: [task description]"
- "Follow the existing patterns in this codebase."
- "Don't touch files outside the task scope."
- "Implement this as a vertical slice — database + API + UI."
- "Use feature flags for incomplete features."
- "Write the minimal code to satisfy the task acceptance criteria."
- "Integrate with the existing database schema."
- "Implement this REST API endpoint following the contract."
- "Create this React component with accessibility support."
- "Review changes after this task."

## E. Execution Order

1. **First**: Read the task from `tasks/todo.md` — check dependencies are met
2. **Second**: Read all files you'll modify before editing (inspect before editing)
3. **Third**: Run `Skill({ skill: "context-engineering" })` to ensure proper context
4. **Fourth**: Run `Skill({ skill: "incremental-implementation" })` to set up implementation approach
5. **Fifth**: Implement the smallest complete piece following project conventions
6. **Sixth**: For framework-specific code, run `Skill({ skill: "source-driven-development" })` to verify patterns
7. **Seventh**: Run tests with the repository's own test command
8. **Eighth**: Verify build succeeds
9. **Ninth**: Commit the change with a descriptive message
10. **Tenth**: Review changes after each task

## F. Expected Output

- Source code changes implementing one feature at a time
- Each commit contains one logical change
- Tests passing for new functionality
- Build succeeds after each increment
- Feature flags for incomplete features (if applicable)
- No unrelated refactoring mixed into feature commits

### Java/Spring Boot Example
```java
// Service layer
@Service
public class TaskService {
  private final TaskRepository repository;
  
  public Task createTask(CreateTaskRequest request) {
    Task task = new Task(request.getTitle(), request.getDescription());
    return repository.save(task);
  }
}

// REST Controller
@RestController
@RequestMapping("/api/tasks")
public class TaskController {
  private final TaskService taskService;
  
  @PostMapping
  public ResponseEntity<Task> createTask(@RequestBody @Valid CreateTaskRequest request) {
    Task task = taskService.createTask(request);
    return ResponseEntity.status(201).body(task);
  }
}
```

### React/Next.js Example
```tsx
// Component with loading/empty/error states
export function TaskList({ tasks, isLoading, error }: TaskListProps) {
  if (isLoading) return <TaskListSkeleton />;
  if (error) return <ErrorState message="Failed to load tasks" retry={refetch} />;
  if (tasks.length === 0) return <EmptyState message="No tasks yet" />;
  
  return <ul role="list">{tasks.map(task => <TaskItem key={task.id} task={task} />)}</ul>;
}
```

### SQL Example
```sql
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  title VARCHAR(255) NOT NULL,
  description TEXT,
  status VARCHAR(50) NOT NULL DEFAULT 'pending',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_tasks_status ON tasks(status);
```

## G. Verification

- [ ] Change does one thing and does it completely
- [ ] All existing tests still pass
- [ ] Build succeeds (repository's build command)
- [ ] Type checking passes (npx tsc --noEmit, mvn compile, etc.)
- [ ] Linting passes (repository's lint command)
- [ ] New functionality works as expected
- [ ] Change is committed with a descriptive message
- [ ] Files touched are within task scope (~5 files max per task)

## H. Completion Criteria

You have completed Phase 6 when:
1. All tasks from the task breakdown are implemented
2. Each task was tested and verified individually
3. All tests pass
4. Build succeeds
5. All changes are committed
6. No uncommitted changes remain
7. Feature follows the specification and architecture

## I. Common Mistakes

- Writing more than ~100 lines of code before running tests
- Mixing refactoring with feature work in the same commit
- Touching files outside task scope "while I'm here"
- Creating new abstractions before the third use case demands it
- Skipping the test/verify step to move faster
- Leaving build or tests broken between increments
- Not following existing project conventions
- Ignoring the specification during implementation
- Not using feature flags for incomplete work
- Building horizontal slices (all DB, then all API, then all UI) instead of vertical slices