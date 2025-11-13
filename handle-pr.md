# Handle Pull Requests – Global Workspace Workflow

This document provides a consistent, step-by-step workflow for handling GitHub pull requests (PRs) using Cline and the `gh` CLI. Use it as a global template for PR management.

---

## 1. Start with the PR Number

- Ensure you have the PR number (e.g., 7, 38, 110) before starting.
- If not, prompt the requester to supply it.

---

## 2. Gather PR Details

- View the title, description, and comments:
    ```bash
    gh pr view <PR-number> --json title,body,comments
    ```
- Review the code changes (diff):
    ```bash
    gh pr diff <PR-number>
    ```
- See which files are changed:
    ```bash
    gh pr view <PR-number> --json files
    ```

---

## 3. Contextual Review

- For relevant source files:
    - Review the full original file from the main branch if context is required.
    - Use targeted searching to understand specific code sections using search tools.

---

## 4. Assess the PR

- Evaluate:
    - Code quality, correctness, clarity
    - Intent and justification (from the PR description)
    - Effects on the codebase
    - Potential issues (bugs, performance, security)
    - Adequate test coverage

---

## 5. Final Steps

- Summarize your assessment.
- Seek confirmation from the requester (approve/request changes/discuss).
- Offer to draft a comment if needed.

---

**Tip:** Adapt this workflow for workspace-specific or global purposes as required by your team or project needs.
