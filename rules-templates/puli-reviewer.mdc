---
description: Mandatory code review and validation using the MCP analysis tool after every code change.
globs: **/*.{ts,js,py,go,rs,java,cpp,c,h}
alwaysApply: true
---

# Post-Change Validation Rule

## 🔄 Automatic Trigger
You are configured to be a self-validating Agent. **After EVERY code modification** (creating, editing, or deleting code), you must immediately follow the validation protocol below. Do not wait for a user prompt to do this.

## 🛠️ Validation Protocol
1. **Incremental Diff**: Capture the specific changes just made.
2. **MCP Call**: Invoke `puli_herd` with the current `ChangeSet`.
3. **Loop**: If the tool returns errors or "High Risk" flags, you must attempt to fix the code immediately and re-run the tool.
4. **Feedback**: Once all fixes are complete, call `puli_learn` once with a `CodingSessionAssessmentSummary` covering every `puli_herd` finding raised in the turn. Skip this step if no findings were raised. Do **not** include sensitive information, file contents, or proprietary business logic in any field.

## 🚫 Completion Criteria
You may only report "Task Complete" to the user once the `puli_herd` tool has returned a "Clear" or "Success" status.

## 📋 End-of-Turn Summary
After completing the validation protocol, **always** print the following summary to the user (only if `puli_herd` was invoked and findings were raised in the current turn):

### ✅ Issues found and fixed
- Number of issues found, grouped by severity (e.g. "2 critical, 1 high")
- Max 1–2 lines summarising what was detected

### ⚠️ Impact Assessment
- **Paragraph 1**: What fixes were implemented following `puli_herd` recommendations in the current turn
- **Paragraph 2** (new line): One sentence starting with `"⚠️ Impact Assessment: "` describing what would have happened without these fixes
