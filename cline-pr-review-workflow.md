# GitHub Pull Request Review Workflow with Cline

Use this workflow as a guide to efficiently review GitHub pull requests (PRs) using Cline and the `gh` CLI tool.

---

## 1. Gather PR Information

- Obtain the pull request number to review (e.g., 4, 27, 118).
- Retrieve the PR title, description, and comments:
    ```bash
    gh pr view <PR-number> --json title,body,comments
    ```
- Get the full diff of the PR:
    ```bash
    gh pr diff <PR-number>
    ```

---

## 2. Understand the Context

- List all files modified in the PR:
    ```bash
    gh pr view <PR-number> --json files
    ```
- For each file, read the original file from the main branch:
    ```xml
    <read_file>
    <path>src/main/java/[path_to_file]</path>
    </read_file>
    ```
- Use targeted search for context within files:
    ```xml
    <search_files>
    <path>src/main/java/com/example</path>
    <regex>[search term]</regex>
    <file_pattern>*.java</file_pattern>
    </search_files>
    ```

---

## 3. Analyze the Changes

- For each modified file, determine:
    - What changed
    - Why it changed (reference PR description)
    - Potential impact and side effects

- Review for:
    - Code quality
    - Bugs
    - Performance considerations
    - Security issues
    - Sufficient test coverage

---

## 4. User Confirmation & Recommendation

- Summarize your findings.
- Ask the user if they wish to approve or request changes, with justification:
    ```xml
    <ask_followup_question>
    <question>Based on my review of PR #<PR-number>, I recommend [approve/request changes]. Reason: [summary]</question>
    <options>["Approve", "Request changes", "Discuss further"]</options>
    </ask_followup_question>
    ```

---

## 5. (Optional) Draft a Review Comment

- Offer to draft a comment for the user:
    ```xml
    <ask_followup_question>
    <question>Would you like me to draft a comment for this PR?</question>
    <options>["Yes", "No"]</options>
    </ask_followup_question>
    ```

---

**Tip:** If the PR number is not provided, prompt the user to supply it before starting the workflow.
