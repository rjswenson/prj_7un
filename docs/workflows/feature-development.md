# Feature Development Workflow

## Overview
Template for developing new features in any of the Project 7UN submodules.

## Pre-Development Checklist

- [ ] Feature requirements clearly defined
- [ ] Target submodule identified (sun-me, sun-online, club-stroll-promo, Taggd.it)
- [ ] Created bead issue: `bd create --title="Feature: ..." --type=feature --priority=2`
- [ ] Checked for dependencies: `bd show <id>`
- [ ] Claimed work: `bd update <id> --status=in_progress`

## Agent Prompt Template

```
I need to implement [FEATURE NAME] in the [SUBMODULE] project.

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Acceptance Criteria:
- [ ] [Criteria 1]
- [ ] [Criteria 2]
- [ ] [Criteria 3]

Please:
1. Review the existing codebase structure in [SUBMODULE]
2. Design the implementation approach
3. Implement the feature following project conventions (see [SUBMODULE]/CLAUDE.md)
4. Write tests if applicable
5. Update documentation as needed
```

## Development Process

### 1. Navigation
```bash
cd [SUBMODULE]
git checkout -b feature/[feature-name]
```

### 2. Implementation
- Follow project-specific guidelines in `[SUBMODULE]/CLAUDE.md`
- Keep changes focused and atomic
- Write tests alongside code (if applicable)
- Follow existing code patterns and conventions

### 3. Quality Checks
```bash
# Run project-specific checks
npm test          # For Node.js projects
npm run lint      # Linting
npm run build     # Build check
```

### 4. Documentation
- [ ] Update relevant README files
- [ ] Add inline code comments where needed
- [ ] Update API documentation if applicable
- [ ] Add examples if appropriate

### 5. Commit
```bash
# In submodule
git add .
git commit -m "Add [feature name]

[Brief description of what and why]

Claude Code | Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# Update parent repo to reference new commit
cd ..
git add [SUBMODULE]
git commit -m "Update [SUBMODULE]: add [feature name]"
```

## Completion Checklist

- [ ] Feature implemented and working
- [ ] Tests written and passing
- [ ] Code follows project conventions
- [ ] Documentation updated
- [ ] Changes committed in submodule
- [ ] Parent repo updated with new submodule reference
- [ ] Bead closed: `bd close <id>`

## Common Pitfalls

- Forgetting to commit in submodule before updating parent
- Not following project-specific naming conventions
- Missing test coverage
- Not updating documentation
- Committing to wrong branch

## Example Session

```bash
# Start
bd ready
bd update prj_7un-xxx --status=in_progress
cd sun-me
git checkout -b feature/dark-mode

# Work with agent
"Implement dark mode toggle in sun-me following the project guidelines..."

# Complete
npm test
git add .
git commit -m "Add dark mode toggle..."
cd ..
git add sun-me
git commit -m "Update sun-me: add dark mode"
bd close prj_7un-xxx
```
