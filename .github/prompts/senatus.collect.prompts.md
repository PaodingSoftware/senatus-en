---
description: Collect manually modified code changes and record them in the task plan
---

## Execution Flow

1. **Check Git Staged Changes**:
   - Run `git diff --cached` to retrieve all changes in the staging area
   - If the staging area is empty, prompt "Please stage your changes using git add first" and terminate the command

2. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitutional constraints

3. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by sequence number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and terminate the command

4. **Read Research Foundation**:
   - Read the `specify/{current-topic-directory}/research.md` file (if it exists)
   - If the research file does not exist, suggest running `/senatus.research` first
   - Analyze the project status based on existing research results

5. **Check Existing Implementation Records**:
   - Check if the `specify/{current-topic-directory}/implementation/` directory exists
   - If implementation record files exist, read all completed implementation content
   - These are completed work and need to serve as reference for analyzing changes

6. **Analyze Code Changes**:
   - Understand the project context based on the topic, existing discussions, research foundation, existing implementation records, and project source code
   - Analyze all changes in the staging area (Git staged)
   - Understand the purpose and scope of impact of the changes
   - Verify whether the changes comply with project constitutional constraints
   - Identify potential risks or considerations that need attention

7. **Generate Change Description**:
   - Automatically generate a concise description based on code changes
   - The description should summarize the core purpose of the changes

8. **Update Task Plan**:
   - Read the `specify/{current-topic-directory}/plan.md` file
   - If the task plan file does not exist, prompt to run `/senatus.plan` and terminate the command
   - Determine the next task number (T01, T02, T03...)
   - Add a new task item to the task list section:
     ```markdown
     T01. [✅Completed] Change description
     ```

9. **Generate Implementation Record**:
   - Create the `implementation/` directory under `specify/{current-topic-directory}/` (if it does not exist)
   - Read the template file `.specify/implementation-template.md`
   - Replace template placeholders:
     - `{{TASK_ID}}` → Task number
     - `{{TASK_DESCRIPTION}}` → Change description
     - `{{IMPLEMENTATION_DETAILS}}` → Detailed change content
     - `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/implementation/{TASK_ID}.md` (overwrite if the file already exists)

## Output Results
- Git staged change statistics (number of files, lines added, lines deleted)
- Generated change description
- New task item number (completed status)
