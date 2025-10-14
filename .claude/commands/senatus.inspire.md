---
description: Inspire new discussion points based on the current topic and project status
---

## Execution Process

1. **Check Project Constitution**:
   - Read the constitution file `specify/constitution.md` (if it exists)
   - Ensure subsequent operations comply with constitution constraints

2. **Get Current Topic**:
   - Scan the `specify/` directory to find the latest topic directory (sorted by number)
   - Read the `discuss.md` file in the latest topic directory to understand the content
   - If no topic directory exists, prompt to run `/senatus.new-topic` and end the command

3. **Read Research Foundation**:
   - Read the `specify/{current-topic-directory}/research.md` file (if it exists)
   - If the research file doesn't exist, suggest running `/senatus.research` first
   - Analyze the project status based on existing research results

4. **Discover Controversial Points**:
   - Comprehensively analyze the topic, existing discussions, research foundation, and project source code
   - Identify technical issues with disagreements or requiring decisions
   - Determine the most valuable controversial point for in-depth discussion

5. **Conduct Discussion**:
   - Begin the discussion based on the identified controversial point, existing discussions, and research results
   - Engage in multiple rounds of dialogue with the user to clarify key questions and technical details
   - Wait for clear user responses; do not conduct self-questioning and self-answering
   - Reference project source code as needed during the discussion
   - **Strictly follow project constitution constraints**

6. **End Discussion**:
   - Stop when a conclusion is reached or the user requests to end
   - Clarify the question discussed and the conclusion reached
   - **Check if the conclusion complies with project constitution requirements**

7. **Record Discussion**:
   - Check the `specify/{current-topic-directory}/discuss.md` file and determine the next number (D01, D02, D03...)
   - Add to the discussion records section in the `specify/{current-topic-directory}/discuss.md` file:
     ```markdown
     ### D[number] - YYYY-MM-DD HH:MM:SS
     **Question**: [Specific question in this discussion]
     **Conclusion**: [Conclusion or decision reached]
     ```
   - **Note**: Do not reference task numbers (such as T01, T02, etc.) in records to avoid ambiguity during rollback

## Output Results
- Discussion summary