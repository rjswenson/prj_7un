# Refactoring Workflow

## Overview
Template for code refactoring in Project 7UN submodules.

## Pre-Refactoring Checklist

- [ ] Refactoring goal clearly defined
- [ ] Tests exist for code being refactored
- [ ] Created bead issue: `bd create --title="Refactor: ..." --type=task --priority=2`
- [ ] Claimed work: `bd update <id> --status=in_progress`

## Agent Prompt Template

```
I need to refactor [CODE/MODULE] in [SUBMODULE].

Current Issues:
- [Issue 1 - e.g., code duplication]
- [Issue 2 - e.g., poor naming]
- [Issue 3 - e.g., complex logic]

Refactoring Goals:
- [Goal 1 - e.g., improve readability]
- [Goal 2 - e.g., reduce complexity]
- [Goal 3 - e.g., improve maintainability]

Constraints:
- Must maintain existing functionality
- Must not break existing tests
- Must follow project conventions

Please:
1. Analyze the current code structure
2. Propose refactoring approach
3. Implement changes incrementally
4. Verify all tests still pass
```

## Refactoring Principles

### The Refactoring Mantra
1. **Ensure tests exist** - If no tests, write them first
2. **Make small changes** - One refactoring at a time
3. **Run tests frequently** - After each change
4. **Commit incrementally** - Small, working commits

### Safe Refactoring Steps

1. **Ensure Test Coverage**
```bash
cd [SUBMODULE]
npm test              # Verify tests pass
npm run test:coverage # Check coverage
```

2. **Create Branch**
```bash
git checkout -b refactor/[description]
```

3. **Refactor Incrementally**
- Extract method
- Rename variables
- Simplify conditionals
- Remove duplication
- One change at a time

4. **Test After Each Change**
```bash
npm test  # After EVERY refactoring step
```

## Common Refactoring Patterns

### Extract Function
```typescript
// Before
function processUser(user) {
  // 50 lines of code
  const validated = /* validation logic */
  const formatted = /* formatting logic */
  const saved = /* save logic */
}

// After
function processUser(user) {
  const validated = validateUser(user);
  const formatted = formatUser(validated);
  return saveUser(formatted);
}
```

### Rename for Clarity
```typescript
// Before
const d = new Date();
function calc(x, y) { }

// After
const currentDate = new Date();
function calculateTotal(price, quantity) { }
```

### Simplify Conditionals
```typescript
// Before
if (user !== null && user !== undefined && user.role === 'admin') { }

// After
if (user?.role === 'admin') { }
```

## Completion Checklist

- [ ] Refactoring completed
- [ ] All tests passing
- [ ] No functionality changed
- [ ] Code is more readable/maintainable
- [ ] No new technical debt introduced
- [ ] Changes committed incrementally
- [ ] Bead closed: `bd close <id>`

## Red Flags - Stop Refactoring If:

- Tests start failing
- You're adding new features (that's not refactoring)
- Changes are getting too large
- You're unsure about the impact
- Scope is expanding beyond original goal

## Example Session

```bash
# Start
bd create --title="Refactor: simplify auth helpers" --type=task
bd update prj_7un-xxx --status=in_progress
cd sun-me
git checkout -b refactor/auth-helpers

# Work with agent
"Refactor the authentication helper functions in src/lib/auth.ts. The code has duplication and complex nested conditionals that make it hard to test..."

# Incremental commits
git commit -m "Extract validateToken function"
npm test
git commit -m "Simplify conditional logic in checkAuth"
npm test
git commit -m "Rename helpers for clarity"
npm test

# Complete
cd ..
git add sun-me
git commit -m "Update sun-me: refactor auth helpers"
bd close prj_7un-xxx
```

## Tips for Working with Agents

- Ask agent to explain why refactoring is needed
- Request incremental changes, not wholesale rewrites
- Have agent run tests after each step
- Ask for before/after comparisons
- Request documentation of what changed and why
