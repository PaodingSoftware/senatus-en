# Senatus Framework

![Senatus Framework](senatus.png)

**Senatus** is a specification-driven development framework designed to provide a complete workflow for requirements analysis, discussion, research, and implementation in software development. Through systematic commands and templates, the framework helps developers manage projects in an orderly manner from initial ideas to final implementation.

Supported AI Programming Assistants:
- Claude Code
- GitHub Copilot

## Core Philosophy

Senatus follows the decision-making model of the ancient Roman Senate, with its core focus on **discussion and documentation**, solving key challenges in AI-assisted development through structured dialogue and documentation processes:

### Core Problems Solved

1. **Insufficient Requirement Expression**: Users often lack details when expressing requirements to AI, leading to AI having to guess user intent
   - Guide users to clarify requirement details through structured discussion
   - Provide precise technical context based on project research
   - Progressively improve requirement understanding through multiple rounds of dialogue

2. **Context Capacity Limitations**: Complex requirements exceed AI context capacity, causing loss of important information
   - Decompose complex requirements into independent discussion topics
   - Systematically record each decision and implementation process
   - Persistently save all key information through documentation system

### Design Principles

- **Specification-Driven**: Ensure all operations comply with established standards through project constitution
- **Progressive Clarification**: From coarse-grained requirements to refined implementation plans
- **Structured Documentation**: Standardized document formats ensure information integrity
- **Traceability**: Completely preserve the entire process from idea to implementation
- **Context Continuity**: Break through single conversation capacity limits through documentation system

## Project Structure

```
senatus/
├── .claude/
│   └── commands/           # Custom command definitions
│       ├── senatus.collect.md      # Collect manual changes
│       ├── senatus.constitution.md # Create project constitution
│       ├── senatus.context.md      # Understand project context
│       ├── senatus.correct.md      # Fix issues
│       ├── senatus.discuss.md      # Topic discussion
│       ├── senatus.dry-run.md      # Dry-run implementation
│       ├── senatus.implement.md    # Execute tasks (batch)
│       ├── senatus.inspire.md      # Inspire discussion
│       ├── senatus.new-topic.md    # Create new discussion topic
│       ├── senatus.plan.md         # Generate task plan
│       ├── senatus.research.md     # Project source code research
│       └── senatus.summary.md      # Topic summary
├── .github/
│   └── prompts/            # GitHub Copilot prompts
│       ├── senatus.collect.prompt.md
│       ├── senatus.constitution.prompt.md
│       ├── senatus.context.prompt.md
│       ├── senatus.correct.prompt.md
│       ├── senatus.discuss.prompt.md
│       ├── senatus.dry-run.prompt.md
│       ├── senatus.implement.prompt.md
│       ├── senatus.inspire.prompt.md
│       ├── senatus.new-topic.prompt.md
│       ├── senatus.plan.prompt.md
│       ├── senatus.research.prompt.md
│       └── senatus.summary.prompt.md
├── .specify/               # Document templates
│   ├── discuss-template.md      # Discussion document template
│   ├── research-template.md     # Research report template
│   ├── plan-template.md         # Task plan template
│   ├── implementation-template.md # Implementation record template
│   └── constitution-template.md # Project constitution template
└── specify/                # Working directory (generated during use)
    ├── constitution.md     # Project constitutional constraints
    └── [number]-[topic-name]/    # Topic working directory
        ├── discuss.md      # Discussion records
        ├── research.md     # Research report
        ├── plan.md         # Task plan
        └── implementation/ # Implementation record directory
            └── [task-number].md
```

## Installation and Configuration

### Prerequisites
- Install an AI programming assistant ([Claude Code](https://claude.com/claude-code) or [GitHub Copilot](https://github.com/features/copilot))
- Ensure the project root directory contains `.claude` and/or `.github` folders

### Usage
1. Copy the Senatus framework files to your project root directory
2. Open your project in a supported AI programming assistant
3. The framework will automatically load all custom commands

## Complete Workflow

### 1. Establish Project Constraints (`/senatus.constitution`)
```bash
/senatus.constitution
```
- Analyze project structure and technology stack
- Generate project constitution file `specify/constitution.md`
- Define technical constraints, quality constraints, security constraints, business constraints
- All subsequent operations must follow these constraints

### 2. Create Discussion Topic (`/senatus.new-topic`)
```bash
/senatus.new-topic Implement user authentication feature
```
- Create a new topic directory (e.g., `specify/001-implement-user-auth/`)
- Generate initial discussion document `discuss.md`
- Assign unique sequence number to the topic

### 3. Project Research (`/senatus.research`)
```bash
/senatus.research
```
- Analyze project source code related to the current topic
- Generate detailed research report `research.md`, including:
  - Technology stack status
  - Code style analysis
  - Related directory structure
  - Business logic analysis
  - Technical implementation approaches

### 4. Topic Discussion (`/senatus.discuss` or `/senatus.inspire` or `/senatus.dry-run`)
```bash
/senatus.discuss Should we use JWT or Session for authentication?
# or
/senatus.inspire
# or
/senatus.dry-run
```
- `/senatus.discuss`: Discuss specific issues
- `/senatus.inspire`: Automatically identify points of contention and inspire discussion
- `/senatus.dry-run`: Dry-run implementation plan, simulate code changes and impacts
- All discussion records will be added to the `discuss.md` file
- Record format: `D01 - Date Time`, including issue and conclusion

### 5. Generate Task Plan (`/senatus.plan`)
```bash
/senatus.plan
# or with additional considerations
/senatus.plan Note to maintain backward compatibility
```
- Generate executable task list based on discussion results and research findings
- Optional: Provide additional considerations or constraints
- Create `plan.md` file containing numbered task items (T01, T02, T03...)
- Each task item has a clear status: ⏳Pending / 🔄In Progress / ✅Completed

### 6. Execute Tasks (`/senatus.implement`)
```bash
# Batch execution (up to 5 tasks)
/senatus.implement
```
- Automatically identify the next task to execute
- `/senatus.implement`: Batch execute up to 5 pending tasks
- Generate implementation records for each completed task
- Update status in the task plan
- Can be run repeatedly until all tasks are completed

### 7. Fix Issues (`/senatus.correct`)
```bash
/senatus.correct Fix session expiration time configuration in user authentication module
```
- Immediately execute issue fixes based on user feedback
- Automatically record the fix process and results
- Add fix entry to discussion records
- Add completed fix task to the task plan
- Generate detailed fix implementation record

### 8. Collect Manual Changes (`/senatus.collect`)
```bash
# First manually modify code and stage
git add .

# Collect changes and record
/senatus.collect
```
- Read Git staged changes (`git diff --cached`)
- Automatically analyze the purpose and impact of staged code changes
- Verify whether changes comply with project constitutional constraints
- Automatically generate change description
- Add changes as completed tasks to the task plan
- Generate detailed implementation record

### 9. Topic Summary (`/senatus.summary`)
```bash
/senatus.summary
```
- Generate complete summary report for the current topic
- Review key technical decisions and discussion results
- Summarize all completed tasks and implementation records
- Analyze project status and remaining issues
- Provide reference for subsequent work

## Command Reference

### `/senatus.collect` - Collect Manual Changes
**Purpose**: Collect user-modified code changes and record them in the framework

**Output**:
- Updated `plan.md` (new completed task added)
- `implementation/[task-number].md` (implementation record)

**Features**:
- Read Git staged changes
- Automatically analyze the purpose and impact of staged changes
- Verify compliance with project constitutional constraints
- Automatically generate change description

### `/senatus.constitution` - Project Constitution
**Purpose**: Create the project's global constraint file

**Output**: `specify/constitution.md`

**Features**:
- Automatically analyze project technology stack
- Generate categorized constraint clauses
- Support version management and history tracking

### `/senatus.context` - Understand Project Context
**Purpose**: Comprehensively understand project context to prepare for subsequent discussions

**Output**: None

**Features**:
- Comprehensively analyze project constitution, topics, research reports, and existing implementation records
- Understand project status based on complete context
- Strictly comply with project constitutional constraints

### `/senatus.correct [issue-description]` - Fix Issues
**Purpose**: Fix project issues based on user feedback

**Parameter**: Issue description (required)

**Output**:
- Updated `discuss.md` (new discussion record added)
- Updated `plan.md` (new completed task added)
- `implementation/[task-number].md` (fix record)

**Features**:
- Precise fixes based on user feedback
- Automatically record fix process and results
- Immediately update discussion and task records

### `/senatus.discuss [discussion-content]` - Topic Discussion
**Purpose**: Conduct structured discussion on specific issues

**Parameter**: Discussion content (required)

**Output**: Add discussion record to `discuss.md`

**Features**:
- Discuss based on project research findings
- Strictly comply with project constitutional constraints
- Automatic numbering and timestamp recording

### `/senatus.dry-run` - Dry-Run Implementation
**Purpose**: Dry-run implementation plan, simulate code changes

**Output**: Add discussion record to `discuss.md`

**Features**:
- Dry-run implementation plan based on research report and discussion results
- Simulate and analyze files and code structures that need to be modified
- Assess implementation complexity, risks, and technical dependencies
- Verify feasibility of technical approach

### `/senatus.implement` - Execute Tasks (Batch)
**Purpose**: Automatically execute pending tasks in batch

**Output**:
- Updated `plan.md` (status update)
- `implementation/[task-number].md` (implementation record)

**Features**:
- Batch execution (up to 5 tasks)
- Automatically generate implementation documentation
- Intelligent progress tracking

### `/senatus.inspire` - Inspire Discussion
**Purpose**: Automatically identify points of contention and inspire valuable discussion

**Output**: Add discussion record to `discuss.md`

**Features**:
- Intelligently identify technical decision points
- Discover issues based on project status
- Guide in-depth technical discussion

### `/senatus.new-topic [topic-description]` - Create New Topic
**Purpose**: Create a structured discussion topic

**Parameter**: Topic description (required)

**Output**: `specify/[number]-[topic-name]/discuss.md`

**Features**:
- Automatically generate kebab-case directory name
- Assign incremental three-digit sequence number
- Create standardized documentation based on template

### `/senatus.plan [considerations]` - Generate Plan
**Purpose**: Transform discussion results into executable task list

**Parameter**: Considerations (optional) - Additional constraints or requirements to consider when generating the plan

**Output**: `specify/[current-topic]/plan.md`

**Features**:
- Generate task items based on all discussion records and research reports
- Support user input of additional considerations
- Arranged in execution order
- Support status tracking
- Strictly comply with project constitutional constraints

### `/senatus.research` - Project Research
**Purpose**: In-depth analysis of project source code, generate research report

**Output**: `specify/[current-topic]/research.md`

**Analysis Content**:
- Technology stack identification
- Code style and architecture patterns
- Related files and directory structure
- Business logic and technical implementation

### `/senatus.summary` - Topic Summary
**Purpose**: Generate complete summary report for the current topic

**Output**: None (directly output summary content)

**Features**:
- Comprehensively analyze discussion records, research reports, task plans, and implementation records
- Summarize key decisions and technical approaches
- Compile completed work and achievements
- Identify remaining issues and improvement opportunities

## Documentation Conventions

### Numbering System
- **Topics**: 001, 002, 003... (three-digit incremental)
- **Discussions**: D01, D02, D03... (D = Discussion)
- **Tasks**: T01, T02, T03... (T = Task)

### Status Indicators
- **⏳Pending**: Task has not started yet
- **🔄In Progress**: Task is partially completed, needs to continue
- **✅Completed**: Task is completed

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

# 6. Dry-run implementation plan
/senatus.dry-run

# 7. Generate task plan
/senatus.plan

# 8. Batch execute tasks (up to 5 tasks at a time)
/senatus.implement
# Can be executed repeatedly until all tasks are completed
/senatus.implement

# 9. Fix issues (if needed)
/senatus.correct Fix configuration issue in user authentication module

# 10. Collect manual changes (if needed)
# Manually modify code...
git add .
/senatus.collect

# 11. Generate topic summary
/senatus.summary
```

### Example of Generated File Structure

```
specify/
├── constitution.md
├── knowledge/
│   └── [knowledge-document].md
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

1. **Always Start with Constitution**: Establish clear constraints for each project
2. **Focus on One Topic at a Time**: Avoid handling multiple complex topics simultaneously
3. **Research Thoroughly Before Discussion**: Ensure decisions are based on accurate project understanding
4. **Record All Points of Contention**: Use `/senatus.inspire` to discover hidden technical issues
5. **Small Steps, Quick Iterations**: Break down large tasks into manageable task items
6. **Maintain Traceability**: Completely preserve all decision processes and implementation records

## Contribution and Support

Senatus Framework is developed and maintained by [PaodingSoftware](https://github.com/PaodingSoftware).

**Project Repository**: https://github.com/PaodingSoftware/senatus

---

*Through Senatus Framework, every technical decision is well-documented, and every implementation is traceable.*