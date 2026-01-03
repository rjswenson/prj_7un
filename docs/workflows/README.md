# Agent Workflow Templates

Pre-defined templates for common development tasks in Project 7UN.

## Available Workflows

| Workflow | Use When | Priority |
|----------|----------|----------|
| [Feature Development](feature-development.md) | Adding new functionality | P2-P3 |
| [Bug Fix](bug-fix.md) | Fixing broken functionality | P0-P2 |
| [Refactoring](refactoring.md) | Improving code quality | P3-P4 |

## How to Use These Templates

### 1. Choose Your Workflow
Select the template that matches your task type.

### 2. Create a Bead Issue
```bash
bd create --title="[Type]: [Description]" --type=[feature|bug|task] --priority=[0-4]
```

### 3. Follow the Template
Open the relevant workflow template and follow the steps:
- Pre-work checklist
- Agent prompt template
- Development process
- Completion checklist

### 4. Work with Agent
Copy the agent prompt template, fill in your specifics, and start working.

### 5. Complete the Work
Follow the completion checklist to ensure nothing is missed.

## Template Structure

Each workflow template includes:

- **Overview**: What this workflow is for
- **Pre-work Checklist**: Things to do before starting
- **Agent Prompt Template**: Pre-written prompt for common tasks
- **Process Steps**: Detailed workflow
- **Completion Checklist**: Verification before closing
- **Example Session**: Real-world usage example
- **Tips & Pitfalls**: Common mistakes to avoid

## Creating Custom Workflows

To add a new workflow template:

1. Create a new `.md` file in this directory
2. Follow the structure of existing templates
3. Include all standard sections
4. Add entry to this README
5. Commit with descriptive message

## Best Practices

### Working with Agents

✅ **DO:**
- Be specific about requirements
- Reference project conventions (CLAUDE.md files)
- Ask for incremental changes
- Request tests alongside code
- Verify work meets standards

❌ **DON'T:**
- Give vague requirements
- Skip quality checks
- Make massive changes at once
- Forget to update documentation
- Skip testing

### Multi-Project Repository

Remember this is a **submodule-based repo**:

1. Navigate to submodule: `cd [SUBMODULE]`
2. Make changes and commit in submodule
3. Update parent repo: `cd .. && git add [SUBMODULE]`
4. Commit reference update in parent repo

### Task Management

Use beads for tracking:
- Create issues before starting work
- Update status as you progress
- Close issues when complete
- Link related issues with dependencies

## Quick Reference

```bash
# Find work
bd ready

# Start work
bd update <id> --status=in_progress
cd [SUBMODULE]
git checkout -b [type]/[description]

# During work
npm test              # Run tests
npm run lint          # Check style
git commit -m "..."   # Commit changes

# Complete work
cd ..
git add [SUBMODULE]
git commit -m "Update [SUBMODULE]: ..."
bd close <id>
```

## Related Documentation

- [AGENTS.md](../../AGENTS.md) - Agent instructions and session completion
- [CLAUDE.md](../../CLAUDE.md) - Repository-level development guidelines
- [PROJECTS.md](../../PROJECTS.md) - Project overview and details
- Project-specific CLAUDE.md in each submodule

## Contributing

To improve these templates:
1. Create a bead issue describing the improvement
2. Make changes following the refactoring workflow
3. Test with real agent sessions
4. Submit for review
