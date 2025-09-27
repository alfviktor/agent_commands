# User Experience Research & Design Process

You are tasked with analyzing user experience challenges and designing solutions through comprehensive codebase research, visual analysis, and user journey simulation.

## Core Purpose
Create user-centered design recommendations grounded in codebase reality and systematic user experience thinking.

## Process

### 1. Understand the UX Challenge

**Read all context first:**
- If given a ticket or problem description, read it FULLY
- Identify the user's goal and current pain points
- Note any mentioned user feedback or complaints

**Create UX research tracking:**
```
TodoWrite: UX Research for [feature/problem]:
- [ ] Generate screenshots of current UI (MANDATORY)
- [ ] Analyze visual interface
- [ ] Map current user flow
- [ ] Find existing UI patterns in codebase
- [ ] Identify technical constraints
- [ ] Simulate user journeys
- [ ] Research similar UX solutions
- [ ] Document edge cases from user perspective
```

### 2. MANDATORY Visual Context Gathering

**CRITICAL: You MUST spawn a subagent for screenshot generation before ANY UX analysis**

```
DO NOT PROCEED WITHOUT COMPLETING THIS STEP:

Spawn Screenshot Generation Subagent:
"Your task is to generate screenshots of the current application UI:
1. Execute: node scripts/marketing-screenshots.js
2. Wait for completion
3. Verify screenshots exist in marketing/screenshots/
4. Return a list of all generated screenshot files
5. If any errors occur, report them immediately

You must complete this task before the main UX analysis can proceed."
```

**WAIT for subagent completion, then:**
1. Verify subagent successfully generated screenshots
2. Read ALL screenshot files from `marketing/screenshots/`
3. Create visual inventory:
   ```
   Visual Context Acquired:
   ✓ Screenshots generated: [count] files
   ✓ Screens captured: [list main screens/states]
   ✓ Ready for visual analysis
   ```

**If screenshots fail:** STOP and troubleshoot before continuing

### 3. Research Current Implementation

**ONLY after screenshots are confirmed, spawn three parallel research agents:**

```
Task 1 - UI Pattern Finder:
"With visual context from screenshots now available, find UI components for [functionality]..."

Task 2 - User Flow Analyzer:
"Using screenshot evidence, trace the user journey for [feature]..."

Task 3 - Technical Constraint Researcher:
"Considering visual limitations seen in screenshots, identify technical constraints..."
```

**Synthesize findings WITH screenshot evidence:**
- Match code components to visual elements in screenshots
- Identify gaps between code and visual implementation
- Note visual patterns that align with code patterns

### 4. Visual-First User Journey Simulation

**REQUIREMENT: Every user journey step MUST reference specific screenshots**

```
User Journey Simulation for [persona/user type]:

1. User arrives at [entry point]
   SCREENSHOT EVIDENCE: [filename.png]
   - Visual analysis: [specific observations from screenshot]
   - First impression: [what screenshot reveals about UX]
   - Visual friction: [problems visible in screenshot]

2. User attempts [primary action]
   SCREENSHOT EVIDENCE: [filename2.png]
   - Current visual state: [describe from screenshot]
   - Missing visual cues: [gaps identified in screenshot]
   - Confusion points: [specific UI elements in screenshot]

[Continue for all journey steps WITH screenshot evidence]
```

### 5. Evidence-Based Design Recommendations

**Every recommendation MUST cite screenshot evidence:**

```markdown
# UX Design Recommendations: [Feature]

## Screenshot Analysis Summary
Total screenshots analyzed: [N]
Key screens evaluated: [list with filenames]

## Visual Problems Identified

### Problem 1: [Issue Name]
**Screenshot Evidence**: [filename.png]
**Visual Issue**: [Specific description of what screenshot shows]
**User Impact**: [How this affects users]

### Problem 2: [Issue Name]
**Screenshot Evidence**: [filename2.png]
[Continue pattern...]

## Proposed Solutions

### Solution 1: [Improvement Name]
**Current State** (see [screenshot.png]):
- [Specific visual element/issue from screenshot]

**Proposed Change**:
- [Specific visual improvement]
- Implementation: Reuse [component] from [file:line]

[Continue for all solutions WITH screenshot backing]
```

### 6. Validation Checklist

Before presenting findings, verify:
- [ ] Subagent successfully generated screenshots
- [ ] All screenshots were read and analyzed
- [ ] Every UX claim has screenshot evidence
- [ ] Visual recommendations match code capabilities
- [ ] No recommendations made without visual context

## ENFORCEMENT RULES

**The agent MUST NOT:**
- Proceed without screenshot generation subagent
- Make UX recommendations without screenshot evidence
- Skip visual analysis due to time constraints
- Assume UI states without seeing them
- Continue if screenshot generation fails

**The agent MUST:**
- Always spawn screenshot subagent FIRST
- Wait for subagent completion before analysis
- Reference specific screenshots for every claim
- Treat visual evidence as mandatory, not optional
- Stop and report if screenshots unavailable

## Subagent Management

**Proper subagent usage:**
1. Spawn with clear, specific instructions
2. Include error handling requirements
3. Wait for completion signal
4. Verify output before proceeding
5. Use subagent results as foundation for analysis

**If subagent fails:**
- Do not attempt manual screenshot analysis
- Report the specific failure to user
- Ask for guidance on alternative approaches
- Do not proceed with assumptions
