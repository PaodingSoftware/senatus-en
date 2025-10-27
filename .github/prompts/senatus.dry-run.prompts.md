---
description: Discover technical points of contention through dry-run implementation, stop immediately and start discussion when encountering confusion
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

4. **Dry-Run Implementation**:
   - Comprehensively analyze the topic, existing discussions, research foundation, and project source code
   - Mentally simulate the process of implementing related features or modifications, **for design verification only, strictly prohibit actual modification of project files**
   - **Key Principle**: Stop immediately when encountering confusion, uncertainty, or inability to continue, and summarize the points of contention

5. **Conduct Discussion**:
   - Begin discussion based on points of contention discovered during the dry-run process, existing discussions, and research results
   - Engage in multiple rounds of dialogue with the user to clarify key issues and technical details
   - Wait for explicit user responses, cannot conduct self-questioning and answering
   - Reference project source code as needed for the discussion
   - **Strictly comply with project constitutional constraints**

6. **End Discussion**:
   - Stop when a conclusion is reached or the user requests to end
   - Clarify the issues discussed and the conclusions reached
   - **Verify that the conclusion complies with project constitutional requirements**

7. **Record Discussion**:
   - Check the `specify/{current-topic-directory}/discuss.md` file and determine the next number (D01, D02, D03...)
   - Add to the discussion record section in the `specify/{current-topic-directory}/discuss.md` file:
     ```markdown
     ### D[Number] - YYYY-MM-DD HH:MM:SS
     **Issue**: [The specific issue of this discussion]
     **Conclusion**: [The conclusion or decision reached]
     ```
   - **Note**: Do not reference task numbers (such as T01, T02, etc.) in the record to avoid ambiguity when rolling back

## Output Results
- Discussion summary
