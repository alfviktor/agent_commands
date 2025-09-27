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
- [ ] Generate screenshots of current UI
- [ ] Analyze visual interface
- [ ] Map current user flow
- [ ] Find existing UI patterns in codebase
- [ ] Identify technical constraints
- [ ] Simulate user journeys
- [ ] Research similar UX solutions
- [ ] Document edge cases from user perspective
```

### 2. Visual Context Gathering

**Generate screenshots for visual analysis:**

Spawn a subagent to capture current UI:
```
Task: Screenshot Generation
"Run the marketing screenshots script to capture current UI states:
1. Execute: node scripts/marketing-screenshots.js
2. Confirm screenshots generated in marketing/screenshots/
3. Return list of generated screenshot files"
```

**After screenshots are generated:**
- Read screenshot files from `marketing/screenshots/` directory
- Analyze each screenshot for:
  - Visual hierarchy
  - Component placement
  - Current interaction patterns
  - Potential confusion points
  - Accessibility issues visible in UI

**Document visual findings:**
```
Visual Analysis of Current UI:
- Screenshot: [filename] shows [what screen/state]
  - Observations: [what works, what doesn't]
  - User attention likely goes to: [element]
  - Potential confusion: [specific UI element/flow]
```

### 3. Research Current Implementation

**Spawn parallel research agents:**

```
Task 1 - UI Pattern Finder:
"Find existing UI components and patterns for [similar functionality]. Look for:
- Component files and their usage
- Styling patterns
- Interaction patterns
- Accessibility implementations"

Task 2 - User Flow Analyzer:
"Trace the current user journey for [feature]. Map:
- Entry points
- Decision points
- Error states
- Success states
Return specific component references"

Task 3 - Technical Constraint Researcher:
"Identify technical limitations affecting UX. Find:
- API response times
- Data structure constraints  
- Performance considerations
- Existing state management"
```

**Synthesize findings with visual context:**
- Current UI components (matched to screenshots)
- Visual patterns that work well
- Visual elements causing friction
- Technical constraints affecting visual design

### 4. Simulate User Experience

**Think through user journeys with visual reference:**

```
User Journey Simulation for [persona/user type]:

1. User arrives at [entry point]
   Visual context from [screenshot.png]:
   - First visual element noticed: [element]
   - Visual hierarchy effectiveness: [analysis]
   - Mental model alignment: [matches/conflicts]

2. User attempts [primary action]
   Current experience per [screenshot2.png]:
   - Visual cues present: [what guides them]
   - Visual friction points: [what confuses]
   - Missing visual feedback: [what's needed]

3. Edge cases (with screenshots where available):
   - Error state visual: [how it appears]
   - Empty state design: [current implementation]
   - Loading visual feedback: [what users see]
   - Mobile responsive issues: [from screenshots]
```

### 5. Design Recommendations

**Present UX solutions grounded in visual analysis:**

```markdown
# UX Design Recommendations: [Feature]

## User Problem
[Clear description with reference to screenshot evidence]

## Visual Analysis Summary
Based on screenshots in `marketing/screenshots/`:
- [screenshot1.png]: Current state shows [issue]
- [screenshot2.png]: User flow reveals [friction point]

## Research Findings
- Current implementation: [UI components at file:line]
- Visual patterns working well: [reference screenshot]
- Visual improvements needed: [specific to screenshots]

## Proposed User Experience

### Visual Hierarchy Improvements
**Current** (see [screenshot.png]): 
- [Element X] dominates but isn't primary action
- [Element Y] is hidden despite importance

**Proposed**: 
- Emphasize [primary action] through [visual technique]
- De-emphasize [secondary elements]
- Add visual cues for [user guidance]

### Interaction Design Improvements
Referencing current states from screenshots:
- **Current hover state**: [barely visible in screenshot]
- **Proposed hover**: [clear visual feedback]
- **Current loading**: [no feedback seen in screenshots]
- **Proposed loading**: [skeleton matching layout]

### Specific Visual Fixes
For issues identified in screenshots:
1. [Screenshot X] shows [problem] → Fix with [solution]
2. [Screenshot Y] lacks [element] → Add [improvement]

## Visual Mockup Notes
Based on screenshot analysis, key visual changes:
- Move [element] to [position] for better flow
- Increase contrast on [component]
- Add visual separator between [sections]
- Implement consistent spacing per [pattern]

## What We're NOT Changing
Visual elements that work well (per screenshots):
- [Element] provides clear feedback
- [Pattern] matches user expectations

## Success Metrics
- Visual hierarchy guides users to [action] first
- Reduced visual clutter in [screenshot area]
- Clear visual feedback for all interactions
- Improved contrast ratio for accessibility
```

### 6. Validate & Iterate

**Present findings with visual evidence:**
```
Based on my analysis of [N] screenshots and UX research:

Key Visual Problems Found:
- [Problem 1]: Screenshot [X] shows users see [issue]
- [Problem 2]: Visual flow in [Y] causes [confusion]

Proposed Visual Solutions:
- [Solution 1]: Improve [element] visibility
- [Solution 2]: Add visual feedback for [action]

Would you like me to:
- Analyze additional UI states?
- Generate more specific screenshots?
- Focus on particular visual issues?
```

## Key Principles

1. **See Before You Design** - Always analyze current visual state via screenshots
2. **Visual Evidence** - Reference specific screenshots in recommendations
3. **User First, Code Second** - Understand visual user needs before implementation
4. **Evidence-Based UX** - Ground recommendations in visual analysis
5. **Respect Visual Patterns** - Follow established visual language

## Visual Analysis Guidelines

**When analyzing screenshots:**
- What draws the eye first? Is it the right thing?
- Where might users get visually lost?
- Is the visual hierarchy supporting the user goal?
- Are interactive elements visually distinct?
- Do visual patterns remain consistent?
- Is there sufficient contrast for accessibility?

**Document visual findings:**
- Screenshot filename and what it captures
- Specific visual problems identified
- Current visual patterns that work
- Visual improvements needed
