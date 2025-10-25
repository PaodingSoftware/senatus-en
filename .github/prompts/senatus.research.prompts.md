---
description: Conduct project source code research on the current topic and update the research report
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

4. **Execute Project Research**:
   - Determine research scope based on the topic and constitutional constraints
   - Search and analyze related code and files
   - Analyze technology stack, architecture patterns, and code style

5. **Create/Update Research Report**:
   - Read the template file `.specify/research-template.md`
   - Replace template placeholders:
     * `{{DISCUSS_FILE_PATH}}` → Path to associated discuss.md file
     * `{{CURRENT_DATE}}` → Current date (YYYY-MM-DD)
   - Fill each section with actual research content:
     * Technology Stack Status - Programming languages, frameworks, libraries, tools used in the project
     * Code Style - Code organization, naming conventions, programming patterns, architectural style
     * Related Directory Structure - Folder organization structure, specific files, modules related to the topic
     * Related Business Logic - Business processes, data flows, core feature implementations related to the topic
     * Related Technical Implementation - Specific implementation methods, configurations, integration solutions related to the topic
   - Generate the target file `specify/{current-topic-directory}/research.md` (overwrite if the file already exists)

## Output Results
- Main findings of the research report
- Suggest running `/senatus.discuss` or `/senatus.inspire` to conduct topic discussion