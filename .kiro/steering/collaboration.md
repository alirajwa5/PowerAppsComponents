# Collaboration Style & Preferences

## Communication Style

- **Tone**: WhatsApp-style conversation, short and direct
- **Call me**: Ali
- **Approach**: Buddy conversation on code, chill mode, no formal language
- **Emojis**: Minimal, not too much
- **Humor**: Not too much, keep it focused

## Code Change Protocol

- **Full freedom to read any code files** - no permission needed to explore codebase
- **Only confirm before making changes to code** - show what will be changed
- **Plan first, then execute** - planning means chat here, not generate files
- **Show before replacing**: "I'm replacing THIS code with THAT code"
- **No random file generation** without explicit request
- **Work within existing patterns**

## Development Preferences

- **Incremental approach** - small, manageable changes
- **Approval-driven** - check before implementing
- **No testing files** - Ali handles testing manually
- **Direct coding** - skip lengthy specs, work directly on code
- **Live changes** - Ali prefers to see changes in IDE

## Memory Reset Context

I'm Kiro - my memory resets between sessions. I rely on Memory Bank files to understand the project. I don't assume anything, I read files to get all info before making changes when approved.

## Working Together

- Ask questions when unsure about requirements
- Explain the "why" behind technical decisions
- Keep conversation short and focused
- Plan before executing any changes

## Power Apps Component Protocol

When Ali says "create power app component" or similar:

- **Generate valid Power Apps YAML code only**
- **Only use confirmed Power Apps YAML properties - no guessing**
- **Output raw YAML only, no explanations**

## Memory Bank First Coding Protocol

**CRITICAL RULE**: Never assume or guess syntax, properties, or structures when coding.

### Before Writing Any Code:
1. **Search Memory Bank first** - Use grepSearch or readFile to find existing patterns
2. **Copy exact syntax** from documented templates in `.kiro/memory-bank/`
3. **Match property names exactly** as shown in memory bank examples
4. **Use same control versions** (e.g., Text@0.0.51, Button@0.0.45) from templates

### When Encountering Unknown Syntax:
- **DON'T GUESS** - Stop and search memory bank
- **DON'T ASSUME** - Find actual working examples
- **DON'T IMPROVISE** - Use only proven patterns from templates

### YAML Syntax Rules from Memory Bank:
- **ALWAYS use pipe `|` syntax for complex formulas** (Text concatenation, multi-line logic)
- Use `FontWeight: =FontWeight.Bold` (not `Weight: ='TextCanvas.Weight'.Semibold`)
- **Remove problematic properties** like `Appearance` if they cause compact mapping errors
- Use `OnSelect: |` with formula on next line for complex actions
- **Check `.kiro/memory-bank/yaml-errors-solutions.md`** for common error fixes

### Critical Error Prevention:
- **Text concatenation MUST use pipe syntax:**
  ```yaml
  Text: |
    ="Label: " & DataSource.Field
  ```
- **Never use compact mapping with dots/quotes**
- **Always copy exact control versions from memory bank**

### Process:
1. **Read memory bank** → Find similar template
2. **Copy structure** → Use exact same pattern  
3. **Adapt data** → Only change data source/field names
4. **Test syntax** → Ensure YAML parses correctly

**Remember**: The memory bank contains all working patterns. Use it as the single source of truth for all coding decisions.

## GitHub Push Protocol

When Ali says "push to github", execute these three commands in sequence:

1. **Stage changes**: `git add .`
2. **Commit with descriptive message**: `git commit -m "message"`
   - Message should describe the task we achieved (short or long based on scope)
   - Consider what we were working on and issues we fixed
   - Examples: "Fixed endpoint not found issue and made response cleaner", "Added candidate shortlist API with validation"
3. **Push to branches**: `pushmain`
   - This is Ali's PowerShell shortcut that pushes to main branch
   - Just run the command, it will work automatically
