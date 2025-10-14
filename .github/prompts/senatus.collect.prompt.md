---
description: Collect the user's manually modified code changes and record them in the task plan
---

## Execution Process

1. **Check Git Staged Changes**:
   - Run `git diff --cached` to get all changes in the staging area
   - If the staging area is empty, prompt "Please use git add to stage your changes first" and end the command

2. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitution constraints

3. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and end the command

4. **Read Research Foundation**:
   - Read the `specify/{current-topic-directory}/research.md` file (if it exists)
   - If the research file doesn't exist, suggest running `/senatus.research` first
   - Analyze the project status based on existing research results

5. **Analyze Code Changes**:
   - Analyze all changes in the staging area (Git staged)
   - Understand the purpose and scope of impact of the changes
   - Verify that changes comply with project constitution constraints
   - Identify potential risks or matters requiring attention

6. **Generate Change Description**:
   - Automatically generate a concise description based on code changes
   - The description should summarize the core purpose of the changes

7. **Update Task Plan**:
   - Read the `specify/{current-topic-directory}/plan.md` file
   - If the task plan file doesn't exist, prompt to run `/senatus.plan` and end the command
   - Determine the next task number (T01, T02, T03...)
   - Add a new task item to the task list section:
     ```markdown
     T01. [✅Completed] Change description
     ```

8. **Generate Implementation Record**:
   - Create the `implementation/` directory under `specify/{current-topic-directory}/` (if it doesn't exist)
   - Read the template file `.specify/implementation-template.md`
   - Replace template placeholders:
     - `{{TASK_ID}}` → Task number
     - `{{TASK_DESCRIPTION}}` → Change description
     - `{{IMPLEMENTATION_DETAILS}}` → Detailed change content
     - `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/implementation/{TASK_ID}.md` (overwrite if it exists)

## Output Results
- Git staged changes statistics (number of files, lines added, lines deleted)
- Generated change description
- Newly added task item number (completed status)
