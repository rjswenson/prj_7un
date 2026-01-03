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

### Important Notes
- Each submodule is an independent git repository
- Changes in submodules must be committed in the submodule first
- Then commit the submodule reference update in the parent repo
- Project-specific guidelines are in each submodule's CLAUDE.md

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

### Workflow
1. Find work: `bd ready`
2. Claim it: `bd update <id> --status=in_progress`
3. Do the work (code, test, commit)
4. Close it: `bd close <id>`
5. Sync beads: `bd sync --from-main` (if on ephemeral branch)

## Development Guidelines

### General Principles
- Keep changes focused and atomic
- Write clear, concise commit messages
- Test before committing
- Follow project-specific conventions (see submodule CLAUDE.md files)

### Commit Message Format
```
Brief summary (imperative mood)

Optional details explaining why (not what - git diff shows what).

Claude Code | Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
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

Each submodule has its own development guidelines:

- **sun-me**: See [sun-me/CLAUDE.md](sun-me/CLAUDE.md) - Next.js portfolio guidelines
- **sun-online**: Check submodule for project-specific docs
- **club-stroll-promo**: Check submodule for project-specific docs
- **Taggd.it**: Legacy Rails project (2013)

## Session Completion Protocol

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

## Common Tasks

### Adding a New Project
```bash
# Add as submodule
git submodule add git@github.com:user/repo.git project-name

# Update PROJECTS.md with project details
# Commit the changes
git add .gitmodules project-name PROJECTS.md
git commit -m "Add project-name submodule"
```

### Working Across Multiple Projects
```bash
# Make changes in submodule
cd sun-me
git checkout -b feature
# ... make changes ...
git commit -m "Add feature"
git push origin feature

# Update parent repo
cd ..
git add sun-me
git commit -m "Update sun-me: add feature"
```

---

**Last Updated:** 2026-01-03
