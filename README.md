# Dev Team Manifesto

## I. Engineering Principles

- **Write Code for Others:** Logical transparency takes priority over complex optimization. Code must be clear to any team member without the author's explanation.
- **Project Autonomy:** Use an intuitive folder structure to make the logic transparent. The project must be self-explanatory so any developer can take over without the author's input. Mandatory English comments must be used to explain complex logic.
- **Atomicity and Naming:** Avoid cumbersome names. Decompose complex logic into small, atomic functions. In narrow contexts, short and precise names (`save`, `fetch`) are preferred.
- **Code Elegance & Conciseness:** Strive for elegant and concise solutions. Elegant code provides maximum clarity with minimal complexity. If a solution feels cluttered or "heavy," it requires refactoring into something more refined.
- **Informed Tech Stack:** Integration of new tools is subject to collective discussion and must be documented in `TECH_STACK.md`.
- **Technical Debt Management:** Temporary solutions ("workarounds") are permitted only if an issue ticket is created in the backlog. The code must include a // TODO comment referencing the specific Ticket ID.
- **Dependency Management:** Adding external packages for atomic functionality is prohibited. Assess package weight and project impact before installation.
- **Boy Scout Rule:** Always leave the code in a better state than you found it.

## II. API Specifications and Mocking (Swagger)

- **Contract-First:** API specifications (OpenAPI) are authored manually in the `api-specs` repository prior to development. The specification serves as the primary contract and the single source of truth.
- **Centralized Documentation:** The `api-specs` repository serves as the single Swagger hub for all projects. A password-protected deployment provides online access for stakeholders.
- **Mandatory Mocking:** Every response schema must include realistic `example` data. This enables frontend development to proceed in parallel using mocks without dependency on backend readiness.

## III. Quality Control (Linters & Automation)

- **Zero Tolerance:** Passing linter checks is a mandatory requirement for code merging. Any static analysis errors or warnings will block Pull Request approval.
- **Automation:** Linting and formatting tools must be integrated into the workflow of every project. Analyzer configurations are unified across the entire team.
- **Pre-commit Hooks:** Husky enforces automated checks (linting, formatting) before commits reach the repository. Bypassing hooks is prohibited.

## IV. AI Usage and Security Policy

- **Accountability:** Developers bear personal responsibility for every line of code. Including AI-generated solutions that are not fully understood by the author is prohibited.
- **Automation Trade-offs:** Speed of generation must not compromise system understanding. Unverified AI code creates hidden technical debt that complicates long-term maintenance.
- **Security:** Transferring proprietary business logic, API keys, or personal data to public AI services is strictly prohibited.

## V. AI Risk Reporting Workflow

*Log AI-related risks using the "AI Risk Report" template in the GitHub Issues of the `dev-manifesto` repo.*

1. **Trigger:** Committing complex or "magical" AI-generated code.
2. **Action:** Create an Issue with the `AI-Risk` label.
3. **Labels & Statuses:**
    - `Review Required`: Default status for new risks pending discussion.
    - `Accepted`: Risk is understood and approved by the team.
    - `Refactor Planned`: Risk is identified, and a refactoring ticket is created.
4. **Format:** Include the Commit Link and Context (Logic details).
5. **Resolution:** Discuss during Code Review. Close only after refactoring or team approval.

## VI. Development Process (GitFlow)

- **Branching:** We follow the Develop / Release model. Direct commits to the `Main` branch are excluded.
- **Branch Naming:** Branch names must match the Jira ticket ID. Create branches directly from Jira tickets to ensure traceability.
- **Conventional Commits:** Commit messages must strictly follow the `<type>`: `<description>` standard.
  *Examples:* `feat: add user authentication`, `fix: resolve login logic error`, `refactor: simplify date helper`, `chore: update dependencies`.
- **Commit Scope:** Soft limit of 400 lines changed per commit. Exceptions are permitted for single logical changes that cannot be reasonably decomposed.
- **Pull Request Discipline:** One pull request per task/issue. PRs must represent a complete, atomic unit of work.
- **Code Review:** Pull Requests to `Develop` require approval from at least one peer. Reviewers are responsible for verifying compliance with this Manifesto.

## VII. Testing Standards

- **Test Pyramid:** Prioritize unit tests for business logic, integration tests for API contracts, and E2E tests (Cypress) for critical user flows.
- **Coverage Philosophy:** Coverage metrics are guidance, not goals. Untested critical paths are defects; tested trivial code is waste.
- **Critical Path Coverage:** High-risk user flows (diagnostic workflows, data integrity operations) require mandatory E2E test coverage.
- **Test Clarity:** Tests are documentation. Test names must describe the expected behavior, not implementation details.
  *Example:* `should reject sample when calibration is expired` > `testValidation3`
- **Test Independence:** Tests must not depend on execution order or shared mutable state.
- **Mocks & Fixtures:** Leverage Swagger examples (Section II) as canonical fixtures to maintain consistency between API contracts and test data.

<!-- TODO: Define unit test framework -->
<!-- TODO: Establish coverage thresholds (qualitative vs. numeric floor) -->
<!-- TODO: Confirm CI gating policy for failing tests -->

---

### 🛠 TECH_STACK.md

| Technology | Status | Rationale | Owner |
|------------|--------|-----------|-------|
| Vue.js | Adopt | Primary frontend framework | — |
| Adobe Spectrum | Adopt | Component library for UI consistency | — |
| Cypress | Adopt | E2E testing framework | — |
| ESLint + security plugins | Adopt | Static analysis with security rules | — |
| Husky | Adopt | Pre-commit hook enforcement | — |

*Statuses: Assess, Trial, Adopt, Hold*