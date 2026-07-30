Improve this skill/spec with the following capabilities:

1. **Atlassian MCP Integration**

   * Use my Atlassian MCP to retrieve the task description automatically.
   * The user should only need to provide the task ID.
   * Fetch all relevant task details before generating the specification.

2. **Dedicated Spec Review Subagent**

   * Create a separate subagent responsible for reviewing the generated specification.
   * Create a dedicated Markdown (`.md`) file that defines this subagent.
   * Configure the subagent to always use GPT-5.6.
   * The reviewer should identify issues, suggest improvements, and validate the quality and completeness of the specification.

3. **God Mode**

   * Support an autonomous "God" mode that never asks the user follow-up questions.
   * Instead, execute the following loop until the specification meets the review criteria:

     1. Inspect the task and gather all available context.
     2. Generate the specification.
     3. Review the specification, categorizing findings into:

        * **Blocking issues** (must be resolved before completion)
        * **Non-blocking issues** (optional improvements)
     4. Resolve all blocking issues.
     5. Update the specification.
     6. Repeat the review cycle until no blocking issues remain.

The final output should be a high-quality specification that has passed the review process with zero blocking issues.
