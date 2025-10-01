# Code Review: Clean Uncommitted Changes

You are tasked with reviewing uncommitted code changes to identify and remove unnecessary additions that don't directly serve the stated goal.

## Initial Setup

When invoked:
1. **Create tracking for the review process:**
   ```
   TodoWrite: Code Cleanup Review
   - [ ] Analyze git diff output
   - [ ] Map changes to requirements
   - [ ] Spawn sub-agents for deep analysis
   - [ ] Run automated quality checks
   - [ ] Generate cleanup recommendations
   - [ ] Execute approved deletions
   ```

2. **Capture the original request from conversation history**
   - What specific problem was being solved?
   - What were the explicit requirements?
   - What was NOT requested?

## Systematic Review Process

### Step 1: Git Analysis

**Run these commands in sequence and analyze output:**

```bash
# Get current repository state
git status -s

# See what files changed and by how much
git diff --stat

# For each file with significant changes (>20 lines), examine:
git diff [filename] | head -50  # Preview changes

# Check for new files
git ls-files --others --exclude-standard

# Look for TODO/FIXME/HACK comments added
git diff | grep -E "TODO|FIXME|HACK|XXX" || true
```

**Document findings:**
```
Change Summary:
- Files modified: [count]
- Lines added: [total]
- Lines removed: [total]
- New files: [list]
- Concerning patterns: [TODOs, debug code, etc.]
```

### Step 2: Spawn Parallel Analysis

**Create three sub-agents for deep analysis:**

```
Task 1 - Unused Code Detector:
"Analyze the git diff output to find:
1. Functions/methods that are defined but never called
2. Imports that are added but not used
3. Variables declared but not referenced
4. Types/interfaces with no usage
Return specific line numbers for removal"

Task 2 - Abstraction Analyzer:
"Review git diff for unnecessary abstractions:
1. Classes/functions used only once
2. Overly generic solutions for specific problems
3. Wrapper functions that add no value
4. Premature optimization patterns
Return complexity score and simplification opportunities"

Task 3 - Scope Creep Detector:
"Compare changes against original requirements:
1. Features added beyond request
2. 'Nice to have' additions
3. Defensive code for unlikely scenarios
4. Infrastructure for future features
Return list of out-of-scope additions"
```

**Wait for all sub-agents to complete**

### Step 3: Run Automated Checks

**Execute quality checks on current state:**

```bash
# Check if changes break anything
npm test 2>&1 | tail -20 || true

# Run linting to find issues
npm run lint 2>&1 | grep -E "warning|error" | head -20 || true

# Check type errors
npm run typecheck 2>&1 | head -20 || true

# Measure complexity (if available)
npm run complexity || true
```

**Document any failures that might be due to unnecessary code**

### Step 4: Build Removal Recommendations

**Create structured analysis:**

```markdown
## Code Review: Unnecessary Code Analysis

### Original Requirement
[Exact requirement from conversation]

### Critical Findings

#### 1. Unused Code (DELETE)
File: `src/utils/helpers.ts`
Lines: 45-67
```typescript
// Current code shown here
```
Reason: Function `formatData` defined but never called
Evidence: No usage found by sub-agent search

#### 2. Over-Abstraction (SIMPLIFY)
File: `src/components/DataManager.ts`
Lines: 12-89
Current: 77 lines for a class used once
Recommended: Inline as 5 lines at usage site

#### 3. Scope Creep (DELETE)
File: `src/api/endpoints.ts`
Lines: 34-98
Feature: Batch processing endpoint
Reason: Original request was for single item processing only

### Automated Check Results
- Tests: ✓ Pass (removing code won't break tests)
- Linting: ⚠️ 12 warnings (mostly in code to be deleted)
- Types: ✓ No errors

### Deletion Summary
Total lines to remove: [X] ([Y]% of additions)
Files to simplify: [count]
Entire functions to delete: [count]
```

### Step 5: Interactive Cleanup

**Present findings and get approval:**

```
Based on systematic analysis:

HIGH CONFIDENCE removals (no impact):
- [X] lines of unused code
- [Y] unnecessary abstractions

MEDIUM CONFIDENCE removals (minor refactor needed):
- [Z] lines of scope creep

Would you like me to:
1. Show detailed diff of proposed deletions
2. Delete HIGH CONFIDENCE items only  
3. Delete all recommended items
4. Skip cleanup
```

### Step 6: Execute Cleanup

**For approved deletions:**

```bash
# For each file, selectively revert unnecessary parts
git checkout -p [filename]

# Or for entire functions/files
git checkout HEAD -- [filename]

# Show the cleaned diff
git diff --stat

# Re-run tests to ensure nothing broke
npm test
```

### Step 7: Final Report

```markdown
## Cleanup Complete

### Before
- Total additions: [X] lines
- Files touched: [Y]
- Complexity: High

### After  
- Net additions: [X-Z] lines
- Files touched: [Y-N]
- Complexity: Appropriate

### What Remains
Only code that directly implements: [original requirement]

### Verification
- ✓ Tests still pass
- ✓ Original feature works
- ✓ No unused code remains
```

## Decision Framework

For each code segment, ask in order:
1. **Is it called?** → If no, DELETE
2. **Does it implement a stated requirement?** → If no, consider DELETE  
3. **Is it the simplest solution?** → If no, SIMPLIFY
4. **Will removing it break anything?** → If no, strong candidate for DELETE
5. **Does it add maintenance burden?** → If yes, needs strong justification

## Common Patterns to Remove

| Pattern | Example | Action |
|---------|---------|--------|
| Debug logging | `console.log('here')` | DELETE |
| Commented code | `// return old_implementation` | DELETE |
| Unused imports | `import { unused } from 'lib'` | DELETE |
| Single-use abstraction | Class with one instance | INLINE |
| Future-proofing | Optional params never used | DELETE |
| Defensive validation | Validating constants | DELETE |
| Copy-paste artifacts | Duplicate similar functions | CONSOLIDATE |

---

Remember: The goal is delivering exactly what was requested with production code. Use systematic analysis, user verification and sub-agents to ensure thorough review before removing anything. Always check with user before deleting anything. 