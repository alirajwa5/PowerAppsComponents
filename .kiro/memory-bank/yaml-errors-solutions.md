# YAML Parsing Errors & Solutions

## Common Power Apps YAML Errors and Their Fixes

### Error 1: Nested mappings are not allowed in compact mappings

**Error Message:**
```
Nested mappings are not allowed in compact mappings at line X, column Y
```

**Cause:** Using complex property syntax in single-line format

**Examples of WRONG syntax:**
```yaml
Weight: ='TextCanvas.Weight'.Semibold
Appearance: ='ButtonCanvas.Appearance'.Secondary
Text: ="First Name: " & SelectedApplicant.'First Name'
```

**CORRECT Solutions:**

1. **For Weight property:**
```yaml
# WRONG
Weight: ='TextCanvas.Weight'.Semibold

# CORRECT
FontWeight: =FontWeight.Bold
```

2. **For Appearance property:**
```yaml
# WRONG  
Appearance: ='ButtonCanvas.Appearance'.Secondary

# CORRECT - Remove the property entirely (use default)
# Or use simple syntax if needed
```

3. **For Text concatenation:**
```yaml
# WRONG
Text: ="First Name: " & SelectedApplicant.'First Name'

# CORRECT - Use pipe syntax for multi-line
Text: |
  ="First Name: " & SelectedApplicant.'First Name'
```

### Error 2: Missing closing quote

**Error Message:**
```
Missing closing "quote at line X, column Y
```

**Cause:** Special characters or complex formulas breaking YAML string parsing

**CORRECT Solution:**
Use pipe `|` syntax for complex formulas:
```yaml
# WRONG
Text: ="Location: " & SelectedApplicant.City & ", " & SelectedApplicant.Country

# CORRECT
Text: |
  ="Location: " & SelectedApplicant.City & ", " & SelectedApplicant.Country
```

### Error 3: Unexpected scalar at node end

**Cause:** Improper YAML structure or missing properties

**Solution:** Follow exact memory bank template structure

### Error 4: Control type not allowed as child

**Error Message:**
```
Control of type 'Classic/Button' is not allowed as a child for control type 'FormViewer'
```

**Cause:** Trying to add incompatible control types as children

**CORRECT Solution:**
Move the button outside the FormViewer as a sibling control:
```yaml
# WRONG - Button inside FormViewer
- FormViewer:
    Children:
      - Button1:
          Control: Classic/Button@2.2.0

# CORRECT - Button as sibling to FormViewer
- FormViewer:
    Children:
      # Only TypedDataCard controls here
- Button1:
    Control: Classic/Button@2.2.0
```

## Memory Bank Proven Patterns

### Text Controls
```yaml
- FieldLabel:
    Control: Label@2.5.1
    Properties:
      Font: =Font.'Open Sans'
      Height: =25
      Size: =14
      Text: |
        ="Label: " & DataSource.Field
      Width: =Parent.Width - 40
```

### Button Controls
```yaml
- ActionButton:
    Control: Button@0.0.45
    Properties:
      Height: =50
      OnSelect: |
        =Navigate(TargetScreen, ScreenTransition.Fade, {Variable: Value})
      Text: ="Button Text"
      Width: =120
```

### Image Controls
```yaml
- ProfileImage:
    Control: Image@2.2.3
    Properties:
      BorderColor: =RGBA(0, 18, 107, 1)
      Height: =200
      Image: =DataSource.'Image Field'
      ImagePosition: =ImagePosition.Fill
      Width: =200
```

## Rules to Prevent These Errors

1. **Always use pipe syntax for complex formulas**
2. **Never use compact mapping syntax with dots/quotes**
3. **Follow exact control versions from memory bank**
4. **Use simple property names (FontWeight vs Weight)**
5. **Test YAML syntax before submitting**

## Why These Errors Happened

**Root Cause:** I was assuming syntax instead of checking memory bank patterns first.

**What I should have done:**
1. Search memory bank for similar controls
2. Copy exact syntax patterns
3. Only modify data source/field names
4. Never guess property syntax

**New Protocol:** Memory Bank First - Always check documented patterns before writing any code.