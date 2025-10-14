---
description: Create the project's constitution file
---

## Execution Process

1. **Check Constitution File**:
   - Check if `specify/constitution.md` exists
   - If it exists, warn that it will be overwritten

2. **Analyze Project Status**:
   - Analyze the project structure and tech stack
   - Identify existing code standards and development patterns

3. **Generate Constraints**:
   - Organize constraints by category headings and list format
   - Common categories: Technical Constraints, Quality Constraints, Security Constraints, Business Constraints

4. **Create Constitution File**:
   - Read the template file `.specify/constitution-template.md`
   - Replace template placeholders:
     * `{{PROJECT_NAME}}` → Project name
     * `{{CONSTITUTION_VERSION}}` → v1.0.0
     * `{{LAST_AMENDED_DATE}}` → Creation date (YYYY-MM-DD)
     * `{{CONSTRAINTS_CONTENT}}` → Generated constraints
     * `{{VERSION_HISTORY}}` → Initial version history record
   - Generate the target file `specify/constitution.md` (overwrite if it exists)

## Output Results
- Constitution file path
- Summary of main constraints