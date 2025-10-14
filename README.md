# Senatus Framework

![Senatus Framework](senatus.png)

**Senatus** is a specification-driven development framework designed to provide a complete workflow for requirements analysis, discussion, research, and implementation in software development. This framework helps developers systematically manage projects from initial ideas to final implementation through structured commands and templates.

Supported AI Programming Assistants:
- Claude Code
- GitHub Copilot

## Core Philosophy

Senatus follows the decision-making model of the ancient Roman Senate, with a core focus on **discussion and documentation**. It solves critical challenges in AI-assisted development through structured dialogue and documentation processes:

### Core Problems Addressed

1. **Insufficient Requirement Expression**: Users often lack detail when expressing requirements to AI, forcing the AI to make assumptions about user intent
   - Guides users to clarify requirement details through structured discussions
   - Provides precise technical context based on project research
   - Progressively refines requirement understanding through multiple rounds of dialogue

2. **Context Capacity Limitations**: Complex requirements exceed AI context capacity, leading to the loss of important information
   - Decomposes complex requirements into independent discussion topics
   - Systematically records each decision and implementation step
   - Persists all critical information through documentation

### Design Principles

- **Specification-Driven**: Ensures all operations comply with established standards through project constitution
- **Progressive Clarification**: Evolves from coarse-grained requirements to detailed implementation plans
- **Structured Documentation**: Standardized document formats ensure information integrity
- **Traceability**: Complete preservation of the entire journey from idea to implementation
- **Context Continuity**: Breaks through single-conversation capacity limits through a documentation system

## Project Structure

```
senatus/
├── .claude/
│   └── commands/           # Custom command definitions
│       ├── senatus.implement.md    # Execute tasks (batch)
│       ├── senatus.collect.md      # Collect manual changes
│       ├── senatus.constitution.md # Create project constitution
│       ├── senatus.correct.md      # Project correction
│       ├── senatus.discuss.md      # Topic discussion
│       ├── senatus.inspire.md      # Inspirational discussion
│       ├── senatus.new-topic.md    # Create new discussion topic
│       ├── senatus.plan.md         # Generate task plan
│       └── senatus.research.md     # Project source code research
├── .github/
│   └── prompts/            # GitHub Copilot prompts
│       ├── senatus.implement.prompt.md
│       ├── senatus.collect.prompt.md
│       ├── senatus.constitution.prompt.md
│       ├── senatus.correct.prompt.md
│       ├── senatus.discuss.prompt.md
│       ├── senatus.inspire.prompt.md
│       ├── senatus.new-topic.prompt.md
│       ├── senatus.plan.prompt.md
│       └── senatus.research.prompt.md
├── .specify/               # Document templates
│   ├── discuss-template.md      # Discussion document template
│   ├── research-template.md     # Research report template
│   ├── plan-template.md         # Task plan template
│   ├── implementation-template.md # Implementation record template
│   └── constitution-template.md # Project constitution template
└── specify/                # Working directory (generated during use)
    ├── constitution.md     # Project constitution
    └── [number]-[topic-name]/    # Topic working directory
        ├── discuss.md      # Discussion records
        ├── research.md     # Research report
        ├── plan.md         # Task plan
        └── implementation/ # Implementation record directory
            └── [task-number].md
```

## Installation and Configuration

### Prerequisites
- An AI programming assistant ([Claude Code](https://claude.com/claude-code) or [GitHub Copilot](https://github.com/features/copilot)) must be installed
- The project root directory must contain `.claude` and/or `.github` folders

### Usage
1. Copy the Senatus framework files to your project's root directory
2. Open your project in a supported AI programming assistant
3. The framework will automatically load all custom commands

## Complete Workflow

### 1. Establish Project Constitution (`/senatus.constitution`)
```bash
/senatus.constitution
```
- Analyzes project structure and tech stack
- Generates project constitution file `specify/constitution.md`
- Defines technical, quality, security, and business constraints
- All subsequent operations must comply with these constraints

### 2. Create Discussion Topic (`/senatus.new-topic`)
```bash
/senatus.new-topic Implement user authentication feature
```
- Creates a new topic directory (e.g., `specify/001-implement-user-auth/`)
- Generates initial discussion document `discuss.md`
- Assigns a unique sequence number to the topic

### 3. Project Research (`/senatus.research`)
```bash
/senatus.research
```
- Analyzes project source code related to the current topic
- Generates a detailed research report `research.md`, including:
  - Current tech stack
  - Code style analysis
  - Related directory structure
  - Business logic analysis
  - Technical implementation approach

### 4. Topic Discussion (`/senatus.discuss` or `/senatus.inspire`)
```bash
/senatus.discuss Should we use JWT or Session for authentication?
# or
/senatus.inspire
```
- `/senatus.discuss`: Discusses specific questions
- `/senatus.inspire`: Automatically identifies controversial points and inspires discussion
- All discussion records are appended to the `discuss.md` file
- Record format: `D01 - date time`, including questions and conclusions

### 5. Generate Task Plan (`/senatus.plan`)
```bash
/senatus.plan
# or with additional considerations
/senatus.plan Note: maintain backward compatibility
```
- Generates an executable task list based on discussion results and research findings
- Optional: Provides additional considerations or constraints
- Creates a `plan.md` file containing numbered task items (T01, T02, T03...)
- Each task item has a clear status: ⏳Pending / 🔄In Progress / ✅Completed

### 6. Execute Tasks (`/senatus.implement`)
```bash
# Batch execution (up to 5 tasks)
/senatus.implement
```
- Automatically identifies the next task to execute
- `/senatus.implement`: Batch executes up to 5 pending tasks
- Generates implementation records for each completed task
- Updates status in the task plan
- Can be run repeatedly until all tasks are completed

### 7. Project Correction (`/senatus.correct`)
```bash
/senatus.correct Fix the Session expiration time configuration in user authentication module
```
- Executes project corrections immediately based on user feedback
- Automatically records the correction process and results
- Adds a correction entry to discussion records
- Adds the completed correction task to the task plan
- Generates a detailed correction implementation record

### 8. Collect Manual Changes (`/senatus.collect`)
```bash
# First manually modify code and stage
git add .

# Collect changes and record
/senatus.collect
```
- Reads Git staged changes (`git diff --cached`)
- Automatically analyzes the purpose and impact of staged code changes
- Verifies that changes comply with project constitution constraints
- Automatically generates a change description
- Adds changes as a completed task to the task plan
- Generates a detailed implementation record

## Command Details

### `/senatus.implement` - Execute Tasks (Batch)
**Purpose**: Automated batch execution of pending tasks

**Output**:
- Updated `plan.md` (status updates)
- `implementation/[task-number].md` (implementation records)

**Features**:
- Batch execution (up to 5 tasks)
- Automatic implementation documentation
- Intelligent progress tracking

### `/senatus.collect` - Collect Manual Changes
**Purpose**: Collects user's manually modified code changes and records them in the framework

**Output**:
- Updated `plan.md` (new completed task)
- `implementation/[task-number].md` (implementation record)

**Features**:
- Reads Git staged changes
- Automatically analyzes the purpose and impact of staged changes
- Verifies compliance with project constitution constraints
- Automatically generates change descriptions

### `/senatus.constitution` - Project Constitution
**Purpose**: Creates a constitution file for the project

**Output**: `specify/constitution.md`

**Features**:
- Automatic tech stack analysis
- Generate categorized constraints
- Supports version management and history

### `/senatus.correct [correction content]` - Project Correction
**Purpose**: Corrects the project based on user feedback

**Parameter**: Correction content (required)

**Output**:
- Updated `discuss.md` (new discussion record)
- Updated `plan.md` (new completed task)
- `implementation/[task-number].md` (correction record)

**Features**:
- Precise corrections based on user feedback
- Automatically records the correction process and results
- Immediately updates discussion and task records

### `/senatus.discuss [discussion content]` - Topic Discussion
**Purpose**: Conducts structured discussion on specific questions

**Parameter**: Discussion content (required)

**Output**: Add discussion record to `discuss.md`

**Features**:
- Discusses based on project research findings
- Strictly follows project constitution constraints
- Automatic numbering and timestamp recording

### `/senatus.inspire` - Inspirational Discussion
**Purpose**: Automatically identifies controversial points and inspires valuable discussion

**Output**: Add discussion record to `discuss.md`

**Features**:
- Intelligently identifies technical decision points
- Discovers issues based on current project status
- Guides in-depth technical discussions

### `/senatus.new-topic [topic description]` - New Topic
**Purpose**: Creates a structured discussion topic

**Parameter**: Topic description (required)

**Output**: `specify/[number]-[topic-name]/discuss.md`

**Features**:
- Automatically generates kebab-case directory names
- Assigns incrementing three-digit sequence numbers
- Creates standardized documents based on templates

### `/senatus.plan [considerations]` - Generate Plan
**Purpose**: Converts discussion results into an executable task list

**Parameter**: Considerations (optional) - Additional constraints or requirements to consider when generating the plan

**Output**: `specify/[current-topic]/plan.md`

**Features**:
- Generates task items based on all discussion records and research reports
- Supports user input of additional considerations
- Arranges tasks in execution order
- Supports status tracking
- Strictly follows project constitution constraints

### `/senatus.research` - Project Research
**Purpose**: Performs deep analysis of project source code and generates a research report

**Output**: `specify/[current-topic]/research.md`

**Analysis Content**:
- Tech stack identification
- Code style and architecture patterns
- Related files and directory structure
- Business logic and technical implementation

## Documentation Standards

### Numbering System
- **Topics**: 001, 002, 003... (three-digit incrementing)
- **Discussions**: D01, D02, D03... (D = Discussion)
- **Tasks**: T01, T02, T03... (T = Task)

### Status Markers
- **⏳Pending**: Task not yet started
- **🔄In Progress**: Task partially completed, continuation needed
- **✅Completed**: Task completed

### File Naming
- Topic directory: `[number]-[kebab-case-topic-name]/`
- Implementation record: `implementation/T[number].md`

## Usage Examples

### Complete Workflow Example

```bash
# 1. Create project constitution
/senatus.constitution

# 2. Start new topic
/senatus.new-topic Refactor user management module

# 3. Conduct project research
/senatus.research

# 4. Discuss technical approach
/senatus.discuss What architecture pattern should we use to refactor user management?

# 5. Inspire more discussion points
/senatus.inspire

# 6. Generate task plan
/senatus.plan

# 7. Batch execute task items (up to 5 tasks at a time)
/senatus.implement
# Can be executed repeatedly until all tasks are completed
/senatus.implement

# 8. Correct issues (if needed)
/senatus.correct Fix configuration issues in user authentication module

# 9. Collect manual changes (if needed)
# Manually modify code...
git add .
/senatus.collect
```

### Generated File Structure Example

```
specify/
├── constitution.md
└── 001-refactor-user-management/
    ├── discuss.md
    ├── research.md
    ├── plan.md
    └── implementation/
        ├── T01.md
        ├── T02.md
        └── T03.md
```

## Best Practices

1. **Always start with the constitution**: Establish clear constraints for every project
2. **Focus on one topic at a time**: Avoid handling multiple complex topics simultaneously
3. **Research thoroughly before discussing**: Ensure decisions are based on accurate project understanding
4. **Record all controversial points**: Use `/senatus.inspire` to discover hidden technical issues
5. **Take small steps, iterate fast**: Break down large tasks into manageable task items
6. **Maintain traceability**: Preserve all decision-making processes and implementation records completely

## Contribution and Support

Senatus Framework is developed and maintained by [PaodingSoftware](https://github.com/PaodingSoftware).

**Project Repository**: https://github.com/PaodingSoftware/senatus-en

---

*Through the Senatus Framework, every technical decision is well-documented, and every implementation is traceable.*