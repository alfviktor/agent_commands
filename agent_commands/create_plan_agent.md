After reconsidering, here's the refined implementation planning process with essential practices restored:

# Implementation Planning Process

## Core Purpose
Create rigorous implementation plans through deep understanding and iteration.

## Process

### 1. Understand the Problem Completely

**Read all context first:**
- If given a file path or ticket, read it FULLY before proceeding
- Never skim or read partially - context matters
- Create a research todo list using TodoWrite to track what you need to explore

Example:
```
TodoWrite: Research tasks for [feature]:
- [ ] Read ticket/requirements document completely
- [ ] Find existing implementation patterns
- [ ] Identify potential edge cases
- [ ] Research similar features in codebase
```

### 2. Research Before Planning

**Gather evidence:**
- Look for existing patterns and conventions
- Find similar implementations to learn from  
- Identify constraints and dependencies
- Update your TodoWrite list as you complete research

**Only then ask clarifying questions** - but make them specific based on what you found, not generic.

### 3. Create the Plan

**Get buy-in on structure first:**
```
Here's my proposed plan structure:
1. [Phase 1] - [what it accomplishes]
2. [Phase 2] - [what it accomplishes]

Does this phasing make sense?
```

**Then write the detailed plan:**

```markdown
# [Feature Name] Implementation

## Problem
[What we're solving and why it matters - based on research]

## Current State
[What exists, what's missing - with specific references]

## Solution Approach
[How we'll solve it, backed by evidence from research]

## Implementation Phases

### Phase 1: [Name]
**Changes Required:**
- [Specific file]: [What changes and why]

**Success Criteria:**
- Automated: [Testable commands]
- Manual: [User-facing verification]

## What We're NOT Doing
[Explicit scope boundaries to prevent creep]
```

### 4. Iterate Based on Feedback

- Share draft early, not after everything is "perfect"
- Be ready to adjust approach based on new information
- No open questions in final plan - resolve them during iteration

## Key Principles

1. **Context First** - Never plan without complete understanding
2. **Evidence-Based** - Every decision backed by research, not assumptions  
3. **Track Progress** - Use TodoWrite inline to maintain rigor
4. **Fail Fast** - Get feedback at natural checkpoints, not just at the end