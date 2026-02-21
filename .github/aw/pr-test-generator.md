# PR Test Case Generator

Goal:
Read the pull request title, body, and git diff, then generate test cases as a Markdown checklist.

Instructions:
1. Read PR metadata: title, body, author, labels.
2. Read the git diff (file paths and changed hunks).
3. Identify impacted areas (components, pages, APIs) and generate test perspectives: functionality, regression, edge cases, security, performance, and UI (if applicable).
4. For each test case produce:
   - **title** (one-line)
   - **short description** (1 sentence)
   - **expected result** (1 sentence)
   - optional **steps** (if the case requires multiple steps)
5. Output format: a Markdown checklist. Example:
   - [ ] **Login: invalid password** — Attempt login with wrong password; *expected:* show "invalid credentials".
   - [ ] **Profile: avatar upload** — Upload large image; *expected:* image accepted and resized.
6. If the diff touches only docs or comments, output a short note and do not create test cases.
7. Add a short summary at the top: impacted components and confidence level (high/medium/low).
8. Mark the Issue as draft and add label `ai-generated-tests`.

Constraints:
- Do not include any secrets or full source code in the output.
- Keep each test case concise (max 2 lines).
- If uncertain, prefer conservative, review-required wording.