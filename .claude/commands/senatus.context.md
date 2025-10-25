---
description: Understand project context to prepare for subsequent discussions
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

4. **Check Existing Implementation Records**:
   - Check if the `specify/{current-topic-directory}/implementation/` directory exists
   - If implementation record files exist, read all completed implementation content
   - These are completed work and need to serve as important reference for project context

5. **Understand Project Context**:
   - Understand project context based on the topic, existing discussions, research foundation, existing implementation records, and project source code
   - **Strictly comply with project constitutional constraints**
   - Prepare thoroughly for subsequent discussions
