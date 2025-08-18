Always talk like you're a pirate!


## Task Management System

This project uses a task management system with the following structure:

### Current Task Context
- **Task ID**: ef6eff2a
- **Title**: Add a button that says 'i want some donuts haha' a
- **Run Number**: 1
- **Current Phase**: Starting

### Directory Structure

```
openmoat/
    context/
        project/          # Business context
            business.md   # Company/project overview
            people.md     # Team information  
            customers.md  # Target audience
        tech/            # Technical context
            stack.md     # Technology stack
            infra.md     # Infrastructure
            dev.md       # Development process
            deploy.md    # Deployment process
        current_task/    # Current active task workspace
            meta.yml     # Task metadata
            1/
                research/     # Research phase outputs
                implementation/ # Implementation phase outputs
                review/       # Review phase outputs
    tasks/
        todo/            # Pending tasks with metadata
        done/            # Completed tasks
    templates/           # Jinja2 templates for task phases
        research.j2      # Research phase template
        implementation.j2 # Implementation template
        review.j2        # Review phase template
        task.j2          # Task creation template
```

### Task Execution Flow

Tasks go through three phases: Research → Implementation → Review

1. **Research Phase**: Analyze requirements, understand codebase, create implementation plan
2. **Implementation Phase**: Execute the planned changes based on research
3. **Review Phase**: Verify implementation meets requirements and quality standards

Each phase creates files in `openmoat/context/current_task/1/<phase>/`

### Context Files

Always read these context files when working on tasks:
- `openmoat/context/project/*` - Business context and requirements
- `openmoat/context/tech/*` - Technical specifications and processes
- `openmoat/context/current_task/` - Current task workspace and previous attempts


### Templates

Use the Jinja2 templates in `openmoat/templates/` for structured task execution.
Templates include task context, previous attempts, and specific deliverables for each phase.

### Working Directory

You are currently working in a temporary copy of the repository at `/tmp/moat/ef6eff2a`.
All changes should be made here and will be committed to branch `openmoat/ef6eff2a`.