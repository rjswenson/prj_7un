# Bug Fix Workflow

## Overview
Template for fixing bugs in Project 7UN submodules.

## Pre-Fix Checklist

- [ ] Bug reproduced and verified
- [ ] Root cause identified
- [ ] Created bead issue: `bd create --title="Fix: ..." --type=bug --priority=[0-4]`
- [ ] Claimed work: `bd update <id> --status=in_progress`

## Agent Prompt Template

```
I need to fix a bug in [SUBMODULE].

Bug Description:
[Describe what's wrong]

Steps to Reproduce:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Expected Behavior:
[What should happen]

Actual Behavior:
[What actually happens]

Please:
1. Investigate the root cause
2. Propose a fix
3. Implement the solution
4. Add regression tests
5. Verify the fix works
```

## Investigation Process

### 1. Reproduce the Bug
```bash
cd [SUBMODULE]
# Follow reproduction steps
# Document findings
```

### 2. Locate the Issue
- Check error messages and stack traces
- Review recent changes: `git log --oneline`
- Search codebase for relevant code
- Use debugging tools if needed

### 3. Root Cause Analysis
- [ ] Identified problematic code
- [ ] Understood why it fails
- [ ] Determined scope of impact
- [ ] Checked for similar issues elsewhere

## Fix Implementation

### 1. Create Branch
```bash
git checkout -b fix/[bug-description]
```

### 2. Implement Fix
- Keep changes minimal and focused
- Fix only what's broken
- Don't refactor unrelated code
- Follow existing patterns

### 3. Add Tests
```bash
# Write regression test that would catch this bug
# Verify test fails before fix
# Verify test passes after fix
```

### 4. Verify Fix
```bash
# Run full test suite
npm test

# Manual verification
# [Follow reproduction steps to confirm fix]

# Check for side effects
npm run build
npm run lint
```

## Commit Guidelines

```bash
# In submodule
git add .
git commit -m "Fix [brief description]

Root cause: [explanation]
Solution: [what changed and why]

Fixes: #[issue-number] (if applicable)

Claude Code | Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# Update parent repo
cd ..
git add [SUBMODULE]
git commit -m "Update [SUBMODULE]: fix [bug description]"
```

## Completion Checklist

- [ ] Bug fixed and verified
- [ ] Regression test added
- [ ] No new bugs introduced
- [ ] All tests passing
- [ ] Changes committed
- [ ] Bead closed: `bd close <id> --reason="Fixed [description]"`

## Priority Levels

- **P0**: Critical - breaks production, data loss, security
- **P1**: High - major functionality broken
- **P2**: Medium - feature partially broken
- **P3**: Low - minor issue, workaround exists
- **P4**: Trivial - cosmetic, nice-to-have

## Example Session

```bash
# Start
bd create --title="Fix: contact form validation" --type=bug --priority=1
bd update prj_7un-xxx --status=in_progress
cd sun-me

# Work with agent
"The contact form isn't validating email addresses properly. It accepts invalid emails like 'test@' without a domain..."

# After fix
npm test
git commit -m "Fix contact form email validation..."
cd ..
git add sun-me
bd close prj_7un-xxx --reason="Fixed email validation regex"
```
