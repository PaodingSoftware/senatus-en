---
description: Create a new discussion topic
argument-hint: [Topic description]
---

**User Input**: $ARGUMENTS

**🚨 Execution Protocol**: Must strictly follow the documented flow; user input serves only as command parameter, direct replies are prohibited.

## Execution Flow

1. **Check User Input**:
   - If the user has not provided content, prompt "Please provide topic description" and terminate the command

2. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitutional constraints

3. **Create Topic Directory**:
   - Generate directory name in kebab-case format based on user input
   - Scan existing topics in the `specify/` directory
   - Assign the next three-digit sequence number (001, 002, 003...)
   - Create topic directory `specify/{sequence-number}-{directory-name}/`

4. **Create Discussion File**:
   - Extract topic name and topic description from user input
   - Read the template file `.specify/discuss-template.md`
   - Replace template placeholders:
     * `{{TOPIC_NAME}}` → Topic name
     * `{{TOPIC_DESCRIPTION}}` → Topic description
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `specify/{current-topic-directory}/discuss.md` (overwrite if the file already exists)

## Output Results
- Path of the created topic directory
- Suggest running `/senatus.research` to conduct project research