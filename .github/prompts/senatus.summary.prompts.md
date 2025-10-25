---
description: Summarize the current topic into a knowledge point
---

## Execution Flow

1. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitutional constraints

2. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by sequence number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and terminate the command

3. **Check Existing Research**:
   - Check if `specify/{current-topic-directory}/research.md` exists
   - If it exists, read the existing content as the foundation

4. **Comprehensively Organize Knowledge Points**:
   - Analyze based on the topic, existing discussions, research foundation, and project source code
   - Comprehensively organize into structured knowledge points

5. **Create Knowledge Point Summary**:
   - Read the template file `.specify/summary-template.md`
   - Replace template placeholders:
     * `{{TOPIC_NAME}}` → Topic name
     * `{{DISCUSS_FILE_PATH}}` → Path to associated discuss.md file
     * `{{SUMMARY_CONTENT}}` → Structured knowledge points formed through comprehensive organization
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Generate the target file `knowledge/{current-topic-directory-name}.md` (overwrite if the file already exists)

## Output Results
- Overview of core summary points
