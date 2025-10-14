---
description: Conduct project source code research on the current topic and update the research report
---

## Execution Process

1. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitution constraints

2. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and end the command

3. **Check Existing Research**:
   - Check if `specify/{current-topic-directory}/research.md` exists
   - If it exists, read the existing content as a foundation

4. **Execute Project Research**:
   - Determine the research scope based on the topic and constitution constraints
   - Search and analyze related code and files
   - Analyze tech stack, architecture patterns, and code style

5. **Create/Update Research Report**:
   - Read the template file `.specify/research-template.md`
   - Replace template placeholders:
     * `{{DISCUSS_FILE_PATH}}` → Associated discuss.md file path
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Fill in actual research content for each section:
     * Current Tech Stack - Programming languages, frameworks, libraries, and tools used in the project
     * Code Style - Code organization, naming conventions, programming patterns, and architecture style
     * Related Directory Structure - Folder organization structure and specific files/modules related to the topic
     * Related Business Logic - Business processes, data flow, and core functionality implementation related to the topic
     * Related Technical Implementation - Specific implementation methods, configurations, and integration solutions related to the topic
   - Generate the target file `specify/{current-topic-directory}/research.md` (overwrite if it exists)

## Output Results
- Main findings of the research report
- Suggest running `/senatus.discuss` or `/senatus.inspire` for topic discussion