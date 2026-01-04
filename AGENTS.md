# Agent Instructions

This project uses **bd** (beads) for issue tracking. Run `bd onboard` to get started.

## Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --status in_progress  # Claim work
bd close <id>         # Complete work
bd sync               # Sync with git
```

## Landing the Plane (Session Completion)

**When ending a work session**, you MUST complete ALL steps below.

**MANDATORY WORKFLOW:**

1. **File issues for remaining work** - Create issues for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **Sync and commit changes** - This is MANDATORY:
   ```bash
   git status              # Check what changed
   git add <files>         # Stage changes
   bd sync --from-main     # Pull beads updates from main
   git commit -m "..."     # Commit with descriptive message
   ```
5. **Verify** - All changes committed, working tree clean
6. **Hand off** - Provide context for next session

**CRITICAL RULES:**
- This repository uses ephemeral branches (no upstream remote)
- Code is merged to main locally, NOT pushed to remote
- Work is NOT complete until all changes are committed
- NEVER skip `bd sync --from-main` - it pulls latest beads updates
- ALWAYS verify `git status` shows clean working tree

Use 'bd' for task tracking

# Project 7UN - Development Guidelines

## Repository Overview

This is a **multi-project repository** containing several independent projects as git submodules under the Project 7UN umbrella.

### Projects

See [PROJECTS.md](PROJECTS.md) for detailed information about each project.

| Project | Type | Tech Stack |
|---------|------|------------|
| sun-me | Portfolio | Next.js, TypeScript |
| sun-online | AI Content Server | Elixir, Python, FastAPI |
| club-stroll-promo | Theatre Promo | Astro |
| Taggd.it | Community | Rails 4.0 |


### Important Notes
- Each submodule is an independent git repository
- Changes in submodules must be committed in the submodule first
- Then commit the submodule reference update in the parent repo
- Project-specific guidelines are in [PROJECTS.md](PROJECTS.md)

## Task Management with Beads

This repository uses **bd (beads)** for issue tracking. See [AGENTS.md](AGENTS.md) for complete workflow.

### Quick Reference
```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --status=in_progress
bd close <id>         # Complete work
bd sync --from-main   # Sync beads (on ephemeral branches)
```

### General Principles
- Keep changes focused and atomic
- Write clear, concise commit messages
- Test before committing
- Follow project-specific conventions
- write tests after confirming functionality

### Commit Message Format
```
Brief summary (imperative mood)

Optional details explaining why (not what - git diff shows what).

Assistant: Claude
```

### Branch Strategy
- `main` - production-ready code
- `develop` - integration branch for features
- Feature branches - specific work, merge to develop

### Quality Standards
- Code must be functional and tested
- No committing of secrets or credentials
- Follow security best practices (XSS, SQL injection, etc.)
- Keep dependencies updated

## Project-Specific Guidelines
See [PROJECTS.md](PROJECTS.md)

Before ending a work session:

1. **Create issues** for remaining work
2. **Run quality gates** (tests, linters, builds) if code changed
3. **Update issue status** - Close finished work
4. **Commit all changes**
   ```bash
   git status              # Check changes
   git add <files>         # Stage changes
   bd sync --from-main     # Sync beads
   git commit -m "..."     # Commit
   ```
5. **Verify** - All changes committed

## Agent Workflow Templates

Pre-defined templates for common development tasks:

- [Feature Development](docs/workflows/feature-development.md) - Adding new functionality
- [Bug Fix](docs/workflows/bug-fix.md) - Fixing broken functionality
- [Refactoring](docs/workflows/refactoring.md) - Improving code quality

See [docs/workflows/README.md](docs/workflows/README.md) for complete guide.

## Documentation

- [PROJECTS.md](PROJECTS.md) - Project overview and details
- [AGENTS.md](AGENTS.md) - Beads workflow and agent instructions
- [Workflow Templates](docs/workflows/) - Agent task templates
- Project-specific docs in each submodule
- [CLAUDE.md](CLAUDE.md) - Claude-specific instructions

## Working with Git Submodules

### Initial Setup
```bash
# Clone with all submodules
git clone --recurse-submodules git@github.com:rjswenson/prj_7un.git

# Or initialize submodules after cloning
git submodule update --init --recursive
```

### Common Submodule Operations
```bash
# Update all submodules to latest commits
git submodule update --remote

# Pull latest changes in each submodule
git submodule foreach git pull origin main

# Work in a specific submodule
cd sun-me
git checkout -b feature-branch
# Make changes, commit, push as normal

# Update parent repo to reference new submodule commit
cd ..
git add sun-me
git commit -m "Update sun-me submodule"
```
