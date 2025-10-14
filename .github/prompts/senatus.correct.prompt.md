---
description: Correct the project based on user feedback and record the process
---

**User Input**: $ARGUMENTS

## Execution Process

1. **Check User Input**:
   - If the user did not provide content, prompt "Please provide specific content to correct" and end the command

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

5. **Execute Project Correction**:
   - Correct based on user input, topic, existing discussions, research foundation, and project source code
   - Analyze the necessity and feasibility of the correction
   - **Strictly follow project constitution constraints**
   - Execute specific correction operations (modify code, configuration, etc.)

6. **Record Discussion**:
   - Check the `specify/{current-topic-directory}/discuss.md` file and determine the next number (D01, D02, D03...)
   - Add to the discussion records section in the `specify/{current-topic-directory}/discuss.md` file:
     ```markdown
     ### D[number] - YYYY-MM-DD HH:MM:SS
     **Question**: [User's correction request]
     **Conclusion**: [Executed correction operation and result]
     ```
   - **Note**: Do not reference task numbers (such as T01, T02, etc.) in records to avoid ambiguity during rollback

7. **Update Task Plan**:
   - Read the `specify/{current-topic-directory}/plan.md` file
   - If the task plan file doesn't exist, prompt to run `/senatus.plan` and end the command
   - Determine the next task number (T01, T02, T03...)
   - Add a new task item to the task list section:
     ```markdown
     T01. [✅Completed] Correction operation description
     ```

8. **Generate Implementation Record**:
   - Create the `implementation/` directory under `specify/{current-topic-directory}/` (if it doesn't exist)
   - Read the template file `.specify/implementation-template.md`
   - Replace template placeholders:
     - `{{TASK_ID}}` → Task number
     - `{{TASK_DESCRIPTION}}` → Correction operation description
     - `{{IMPLEMENTATION_DETAILS}}` → Detailed correction details (including modified code segments)
     - `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/implementation/{TASK_ID}.md` (overwrite if it exists)

## Output Results
- Description of executed correction operation
- Newly added discussion record number
- Newly added task item number (completed status)