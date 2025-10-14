---
description: Create a new discussion topic
---

**User Input**: $ARGUMENTS

## Execution Process

1. **Check User Input**:
   - If the user did not provide content, prompt "Please provide topic description" and end the command

2. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitution constraints

3. **Create Topic Directory**:
   - Generate a kebab-case format directory name based on user input
   - Scan existing topics in the `specify/` directory
   - Assign the next three-digit sequence number (001, 002, 003...)
   - Create the topic directory `specify/{number}-{directory-name}/`

4. **Create Discussion File**:
   - Extract the topic name and topic description from user input
   - Read the template file `.specify/discuss-template.md`
   - Replace template placeholders:
     * `{{TOPIC_NAME}}` → Topic name
     * `{{TOPIC_DESCRIPTION}}` → Topic description
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/discuss.md` (overwrite if it exists)

## Output Results
- Created topic directory path
- Suggest running `/senatus.research` for project research