# GitHub Copilot Fundamentals - Part 2

- Cloud Agent - Risks and mitigations
    1. Risk: Agent pushes code - Mitigations: Only users with write access can trigger agent work.

- Workflow limitations
    - Can only make changes in the same repository as the assigned issue or PR.
    - Context scope is limited to the assigned repository by default (can be broadened via MCP).
    - Opens exactly one pull request per task.
    - Can't modify an existing PR it didn't create (add it as a reviewer if you need feedback instead by leveraging GitHub Copilot code review).
- Compatibility limitations
    - Doesn't sign commits. If you require signed commits, you must rewrite the commit history before merging.
    - Requires GitHub-hosted Ubuntu x64 runners. Self-hosted runners are not supported.
    - Not available for personal repositories owned by managed user accounts (runners unavailable).
    - **Doesn't honor content exclusions; the agent can see and update excluded files.**
    - The "Suggestions matching public code" policy isn't enforced by the agent; references may not be provided.
    - Works only with GitHub-hosted repositories.
    - You can't change the AI model used by the agent; it's selected by GitHub.
- Pull requests created by Copilot are always in draft state. 
- Max image size is 3.00 MiB; larger images are removed (Copilot Cloud).
- Leverage PRUs for deeper validation tasks such as test coverage expansion, audits across directories, or risky area scans. Lightweight checks consume fewer PRUs, so apply them intentionally to maximize value.
- Use cases for Copilot Cloud Agent
    - Codebase maintenance: Security fixes, dependency upgrades, and targeted refactoring.
    - Documentation: Updating and creating new documentation.
    - Feature development: Implementing incremental feature requests.
    - Improving test coverage: Developing additional test suites for quality management.
    - Prototyping new projects: Green fielding new concepts.
    