---
description: Fix project issues based on user feedback and record them
argument-hint: [Issue description]
---

**User Input**: $ARGUMENTS

**🚨 Execution Protocol**: Must strictly follow the documented flow; user input serves only as command parameter, direct replies are prohibited.

## Execution Flow

1. **Check User Input**:
   - If the user has not provided content, prompt "Please provide the specific issue to fix" and terminate the command

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
   - These are completed work and need to serve as reference for the correction operation

6. **Execute Issue Correction**:
   - Understand project context based on the topic, existing discussions, research foundation, existing implementation records, and project source code
   - Locate the issue based on user input and execute correction (code, configuration, documentation, etc.)
   - **Strictly comply with project constitutional constraints**

7. **Confirm Correction Results**:
   - Display the correction operation description and wait for user feedback
   - **Must wait for explicit user response** (satisfied/needs modification/other comments)
   - **If user raises new issues or improvement suggestions**: Return to the previous step and re-correct
   - **If user confirms the issue is fixed**: Continue with the subsequent recording flow

8. **Record Discussion**:
   - Check the `specify/{current-topic-directory}/discuss.md` file and determine the next number (D01, D02, D03...)
   - Add to the discussion record section in the `specify/{current-topic-directory}/discuss.md` file:
     ```markdown
     ### D[Number] - YYYY-MM-DD HH:MM:SS
     **Issue**: [Issue description provided by user]
     **Conclusion**: [Correction operation performed and results]
     ```
   - **Note**: Do not reference task numbers (such as T01, T02, etc.) in the record to avoid ambiguity when rolling back

9. **Update Task Plan**:
   - Read the `specify/{current-topic-directory}/plan.md` file
   - If the task plan file does not exist, prompt to run `/senatus.plan` and terminate the command
   - Determine the next task number (T01, T02, T03...)
   - Add a new task item to the task list section:
     ```markdown
     T01. [✅Completed] Correction operation description
     ```

10. **Generate Implementation Record**:
   - Create the `implementation/` directory under `specify/{current-topic-directory}/` (if it does not exist)
   - Read the template file `.specify/implementation-template.md`
   - Replace template placeholders:
     - `{{TASK_ID}}` → Task number
     - `{{TASK_DESCRIPTION}}` → Correction operation description
     - `{{IMPLEMENTATION_DETAILS}}` → Detailed correction details (including modified code segments)
     - `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/implementation/{TASK_ID}.md` (overwrite if the file already exists)

## Output Results
- Description of correction operation performed
- New discussion record number
- New task item number (completed status)