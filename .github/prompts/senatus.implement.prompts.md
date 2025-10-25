---
description: Automatically identify current progress and execute multiple tasks in batch
---

## Execution Flow

1. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitutional constraints

2. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by sequence number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and terminate the command

3. **Read Research Foundation**:
   - Read the `specify/{current-topic-directory}/research.md` file (if it exists)
   - If the research file does not exist, suggest running `/senatus.research` first
   - Analyze the project status based on existing research results

4. **Read Task List**:
   - Read the `specify/{current-topic-directory}/plan.md` file
   - If the task file does not exist, prompt to run `/senatus.plan` and terminate the command
   - Parse the task list and extract all task items and their statuses

5. **Identify Tasks to Execute**:
   - Look for "⏳Pending" or "🔄In Progress" task items (by number T01, T02, T03...)
   - If all tasks are completed, display completion status and terminate the command
   - Prioritize "🔄In Progress" tasks, then take up to 5 pending tasks in sequential order

6. **Read Implementation Records**:
   - Read implementation records of completed tasks in the `specify/{current-topic-directory}/implementation/` directory (if they exist)

7. **Execute Tasks in Batch**:
   - For each task to be executed:
     * Comprehensively analyze task description, topic, existing discussions, research foundation, and implementation records
     * Develop implementation plan in conjunction with project source code and code structure
     * **Strictly comply with project constitutional constraints**
     * Progressively implement changes and verify through testing
     * Update status to "✅Completed" or "🔄In Progress" based on completion

8. **Generate or Update Implementation Records**:
   - Generate or update implementation records for each executed task:
     * Create the `implementation/` directory under `specify/{current-topic-directory}/` (if it does not exist)
     * Read the template file `.specify/implementation-template.md`
     * Replace template placeholders:
       - `{{TASK_ID}}` → Task number
       - `{{TASK_DESCRIPTION}}` → Task description
       - `{{IMPLEMENTATION_DETAILS}}` → Detailed implementation details (including modified code segments; if 🔄In Progress, explain completed and incomplete portions)
       - `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
     * Generate the target file `specify/{current-topic-directory}/implementation/{TASK_ID}.md` (overwrite if the file already exists)

9. **Update Task Plan**:
   - Update the status of all completed tasks in the `specify/{current-topic-directory}/plan.md` file

## Output Results
- Task numbers and descriptions executed
- Completion status of each task (✅Completed or 🔄In Progress)
- If there are 🔄In Progress tasks, explain the completed and incomplete portions
- If there are still pending tasks, suggest continuing to execute `/senatus.implement`