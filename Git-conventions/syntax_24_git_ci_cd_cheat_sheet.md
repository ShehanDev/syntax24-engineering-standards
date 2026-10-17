# Syntax 24: Git & CI/CD Cheat Sheet

A comprehensive developer reference for version control, branching strategies, commit standards, CI/CD pipelines, and merge workflows.

---

## 1. Initial Push to Hub
Getting a brand new local project up to a remote repository involves initializing Git, staging your files, creating your first commit, and linking the remote hub.

<Image alt="Diagram showing files moving from working directory to staging area, local repository, and finally remote repository via git push" caption="Git working directory to remote push" src="image_agent_tag_9800439259790656066"/>

**Standard Commands:**
```bash
# Initialize the local repository
git init

# Set the default primary branch name to main
git branch -M main

# Stage all project files
git add .

# Create the initial commit
git commit -m "chore: initial project setup"

# Link to your remote hub repository
git remote add origin <remote-repository-URL>

# Push the code to the main branch
git push -u origin main
```

---

## 2. Repository & Branching Strategies
A structured branching strategy keeps the codebase stable while allowing multiple engineers to develop features in parallel. No developer should ever commit directly to `prod` or `master`.

<Image alt="Git branching strategy diagram showing main, develop, and feature branches" caption="Standard branching workflow" src="image_agent_tag_9800439259790657075"/>

### Core Permanent Branches
*   **`main` / `prod`:** The source of truth. This branch holds the official, stable release history. Code here is actively running in production. 
*   **`develop` / `dev`:** The primary integration branch. All completed feature branches are merged here first.

### Temporary Branches
*   **`feat/*` (Feature):** For building a new feature. Branches off `dev` and merges back into `dev`.
*   **`bugfix/*` (Bugfix):** For resolving issues found in `dev` during development/testing.
*   **`hotfix/*` (Hotfix):** For critical production bugs. Branches directly off `prod` and merges back into both `prod` and `dev`.

### 5 Feature Branch Examples
When naming feature branches, use the `feat/` prefix followed by a highly descriptive, hyphen-separated name:
1.  `feat/oauth2-login` (Adding Google/GitHub login capabilities)
2.  `feat/user-dashboard-ui` (Building the main interface for logged-in users)
3.  `feat/pdf-invoice-export` (Allowing users to download their billing history)
4.  `feat/stripe-payment-gateway` (Integrating the payment processing API)
5.  `feat/realtime-chat-websocket` (Adding live messaging support)

<Image alt="Diagram showing a feature branch diverging from the main branch, receiving commits, and then merging back into the main branch via a pull request." caption="Feature branch diverging and merging back via pull request" src="image_agent_tag_8566503229105109036"/>

---

## 3. Commit Strategies (Conventional Commits)
Standardizing commit messages allows you to understand exactly what a change does at a glance and makes automated changelog generation much easier. The format generally follows `<type>(<scope>): <subject>`.

<Image alt="Structure of a conventional commit showing type, scope, and description" caption="Conventional Commit Structure" src="image_agent_tag_9800439259790657095"/>

**Syntax 24 Type Convention Rules:**
*   **feat:** Indicates the development of a new feature for the project. *(Example: Adding a service, functionality, endpoint, etc.)*
*   **fix:** Used when correcting errors that are generating bugs in the system. *(Example: Apply a handling for a function that is not behaving as expected and returning an error.)*
*   **refactor:** Used when there is a code refactoring that does not have any impact on the system logic/rules. *(Example: Code changes after a code review)*
*   **style:** Used when there are code formatting and style changes that do not change the system in any way. *(Example: Change the style-guide, change the lint convention, fix indentations, remove white spaces, etc.)*
*   **test:** Indicates any type of creation or alteration of test codes. *(Example: Creation of unit tests.)*
*   **chore:** Indicates changes to the project that do not affect the system or test files. These are developmental changes. *(Example: Change rules for eslint, add prettier, update .gitignore)*
*   **docs:** Used when there are changes in the project documentation. *(Example: add information in the API documentation, change the README, etc.)*
*   **build:** Used to indicate changes that affect the project build process or external dependencies. *(Example: add/remove npm dependencies)*
*   **perf:** Indicates a change that improved system performance. *(Example: change ForEach to While)*
*   **ci:** Used for changes in CI configuration files. *(Example: Circle, Travis, GitHub Actions configs)*
*   **revert:** Indicates the reversal of a previous commit.

---

## 4. CI/CD Workflows for Frontend & Backend
Continuous Integration (CI) and Continuous Deployment (CD) automate the testing and delivery of your code to ensure high quality and fast releases.

<Image alt="CI/CD architecture diagram showing code, build, test, release, and deploy stages" caption="Standard CI/CD pipeline architecture" src="image_agent_tag_9800439259790658104"/>

**Frontend Workflow (e.g., React / Vue / Flutter):**
1.  **Code Quality:** Run Linters and static analysis.
2.  **Test:** Execute unit and component tests to verify UI logic.
3.  **Build:** Bundle the assets for production (compiling JS, generating minified bundles).
4.  **Deploy:** Push the built artifacts to a CDN or cloud storage.

**Backend Workflow (e.g., Java Spring Boot / Node.js API):**
1.  **Test:** Run unit and integration tests.
2.  **Build:** Compile the application into an executable artifact.
3.  **Containerize:** Build a Docker image with the newly compiled application.
4.  **Deploy:** Push the Docker image to a registry and trigger an update in the deployment environment (e.g., Kubernetes).

---

## 5. Merging Strategies (--no-ff Merge Commit Workflow)
To maintain a clean, auditable history, feature branches should be integrated using Non-Fast-Forward merges (`--no-ff`). 

<Image alt="Diagram showing the difference between a standard merge commit and a squash merge" caption="Merge Commit vs. Squash Merge" src="image_agent_tag_9800439259790659133"/>

**Why use `--no-ff`?**
It groups all the commits from that feature together under a single merge bubble in your Git graph. If a bug is discovered later, you can easily trace it back to the specific feature branch and revert the entire merge commit at once, rather than hunting down individual commits.

**Command Line Execution for Feature Merge:**
```bash
# 1. Ensure you are on the dev branch and it is up to date
git checkout dev
git pull origin dev

# 2. Merge the feature branch and force a merge commit
git merge --no-ff feat/oauth2-login -m "Merge: feat/oauth2-login into dev"

# 3. Push the updated dev branch to the remote hub
git push origin dev

# 4. Delete the local feature branch (cleanup)
git branch -d feat/oauth2-login
```