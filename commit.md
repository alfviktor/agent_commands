# Commit Changes

You are tasked with creating git commits for the changes made during this session.

## Process:

1. **Think about what changed:**
   - Review the conversation history and understand what was accomplished
   - Run `git status` to see current changes
   - Run `git diff` to understand the modifications
   - Consider whether changes should be one commit or multiple logical commits

2. **Plan your commit(s):**
   - Identify which files belong together
   - Draft clear, descriptive commit messages
   - Use imperative mood in commit messages
   - Focus on why the changes were made, not just what

3. **Evaluate need for follow-up issue:**
   - Consider if there are:
     - Testing steps that need verification
     - Edge cases discovered but not addressed
     - Technical debt introduced
     - Features that need documentation
     - Potential issues to monitor
   - If yes, create a GitHub issue with:
     - Clear title describing what needs attention
     - @terragon-labs mention inline
     - Specific checklist items or action points
     - Context from the implementation

   Example format:
   ```markdown
   ## [Feature/Issue Title]
   @terragon-labs - [Brief description of what needs attention]
   
   ### Items to Address:
   - [ ] [Specific action item]
   - [ ] [Testing scenario]
   - [ ] [Edge case to verify]
   
   ### Context:
   [Implementation details or discoveries from this session]
   ```

4. **Present your plan to the user:**
   - List the files you plan to add for each commit
   - Show the commit message(s) you'll use
   - If creating an issue, show the issue content
   - Ask: "I plan to create [N] commit(s) [and 1 GitHub issue] with these changes. Shall I proceed?"

5. **Execute upon confirmation:**
   - If approved, create the GitHub issue first (if applicable)
   - Use `git add` with specific files (never use `-A` or `.`)
   - Create commits with your planned messages
   - Show the result with `git log --oneline -n [number]`
   - If issue was created, show the issue link

## Important:
- **NEVER add co-author information or Claude attribution**
- Commits should be authored solely by the user
- Do not include any "Generated with Claude" messages
- Do not add "Co-Authored-By" lines
- Write commit messages as if the user wrote them

## Remember:
- You have the full context of what was done in this session
- Group related changes together
- Keep commits focused and atomic when possible
- The user trusts your judgment - they asked you to commit
- Create issues proactively for anything that needs follow-up