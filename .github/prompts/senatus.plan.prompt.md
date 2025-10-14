---
description: Generate an executable task list based on the current topic
---

**User Input**: $ARGUMENTS

## Execution Process

1. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitution constraints

2. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and end the command

3. **Read Research Foundation**:
   - Read the `specify/{current-topic-directory}/research.md` file (if it exists)
   - If the research file doesn't exist, suggest running `/senatus.research` first
   - Analyze the project status based on existing research results

4. **Check Existing Implementation Records**:
   - Check if the `specify/{current-topic-directory}/implementation/` directory exists
   - If implementation record files exist, read all completed implementation content
   - Count the maximum number of existing implementation records (e.g., T05) and determine the starting number
   - These are the work completed before the previous rollback; subsequent tasks need to be generated based on this

5. **Generate Task List**:
   - Analyze based on the topic, existing discussions, research foundation, existing implementation records, and project source code
   - **If there is user input, incorporate it as considerations**
   - Organize all conclusions and decisions, and identify specific task items
   - **Strictly follow project constitution constraints**
   - Arrange tasks in execution order and assign numbers:
     * If there are existing implementation records, start from maximum number + 1 (e.g., if T05 exists, start from T06)
     * If no existing implementation records, start from T01

6. **Create Task Plan**:
   - Read the template file `.specify/plan-template.md`
   - Replace template placeholders:
     * `{{DISCUSS_FILE_PATH}}` → Associated discuss.md file path
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Fill in the generated task list in the task list section:
     ```markdown
     T01. [⏳Pending] Task description
     T02. [⏳Pending] Task description
     T03. [⏳Pending] Task description
     ```
   - **Note**: If there are implemented tasks, list them together (status ✅Completed)
   - Generate the target file `specify/{current-topic-directory}/plan.md` (overwrite if it exists)


## Output Results
- Number of generated task items
- Suggest running `/senatus.implement` to start implementation