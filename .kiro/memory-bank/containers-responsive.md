# Power Apps Responsive Containers Guide

## Key Properties for Responsive Design

### Critical Responsive Properties

**LayoutWrap: =true** - This is the MAGIC property that makes containers responsive!
- When containers don't fit horizontally, they wrap to the next line
- Essential for mobile responsiveness

### GroupContainer@1.3.0 Proven Properties

#### Main Container Structure:
```yaml
- mainContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      Height: =Parent.Height
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      LayoutJustifyContent: =LayoutJustifyContent.SpaceBetween
      LayoutWrap: =true  # KEY FOR RESPONSIVENESS
      Width: =Parent.Width
```

#### Content Container (Horizontal with Wrapping):
```yaml
- ContentContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Horizontal  # Side by side on large screens
      LayoutWrap: =true  # WRAPS TO VERTICAL ON SMALL SCREENS
```

#### Individual Containers:
```yaml
- Container:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      LayoutJustifyContent: =LayoutJustifyContent.SpaceBetween
      LayoutWrap: =true  # Optional for nested responsiveness
```

### Text@0.0.51 Proven Properties

```yaml
- TextLabel:
    Control: Text@0.0.51
    Properties:
      AlignInContainer: =AlignInContainer.Center
      AutoHeight: =true  # NEW PROPERTY - Auto adjusts height
      Size: =48
      Text: ="Label Text"
      Weight: ='TextCanvas.Weight'.Bold
```

### Header@0.0.44 Proven Properties

```yaml
- Header:
    Control: Header@0.0.44
    Properties:
      Title: ="Header Title"
```

## How Responsiveness Works

### Large Screens:
- `LayoutDirection: =LayoutDirection.Horizontal` keeps containers side by side
- Containers A, B, C appear horizontally: **A | B | C**

### Small Screens:
- `LayoutWrap: =true` makes containers wrap when they don't fit
- Containers stack vertically:
  ```
  A
  B  
  C
  ```

## Responsive Design Pattern

1. **Main Container**: Vertical layout with `LayoutWrap: =true`
2. **Content Container**: Horizontal layout with `LayoutWrap: =true`
3. **Individual Containers**: Vertical layout for internal content
4. **Text Controls**: Use `AutoHeight: =true` for flexible sizing

## Key Differences from Previous Code

### What Changed for Responsiveness:
- **Added `LayoutWrap: =true`** to main and content containers
- **Added `AutoHeight: =true`** to text controls
- **Removed fixed `Height` and `FillPortions`** from individual containers
- **Simplified structure** for better wrapping behavior

### Properties That Make It Responsive:
1. `LayoutWrap: =true` - Essential for wrapping
2. `LayoutDirection: =LayoutDirection.Horizontal` - Side by side on large screens
3. `AutoHeight: =true` - Flexible text sizing
4. `LayoutAlignItems: =LayoutAlignItems.Stretch` - Consistent sizing

## Responsive Testing Checklist

✅ Large screen: Containers side by side
✅ Medium screen: Some containers wrap
✅ Small screen: All containers stack vertically
✅ Text scales properly with AutoHeight
✅ No horizontal scrolling on mobile

**Remember: `LayoutWrap: =true` is the key to Power Apps responsiveness!**# Pow
er Apps Container Design - YouTube Video Insights

## Key Benefits of Container Controls

### 1. Structured App Layouts
**Problem with First Generation Apps:**
- Controls positioned manually relative to screen
- All controls independent of each other
- Hard to maintain and update
- Manual padding and spacing for every control

**Container Solution:**
- Controls positioned relative to parent container
- Automatic padding and spacing
- Automatic size/position adjustment based on available space
- Enables responsive design

### 2. Root Container Setup
**Essential First Step:**
```yaml
- RootContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      Height: =Parent.Height
      Width: =Parent.Width
      X: =0
      Y: =0
```

### 3. Layout Design Process

#### Step 1: Break Down Into Wireframes
- Look at your design and identify sections
- Break down into wireframe components
- Determine if sections stack vertically or horizontally

#### Step 2: Choose Root Container Direction
**Key Question:** "How can I break down this layout along only one axis in a way that none of the sections are split?"

**Examples:**
- Header + Content + Footer = Vertical container
- Sidebar + Main Content = Horizontal container

#### Step 3: Apply Recursively
- Each container can contain other containers
- Use same process for each sub-section
- Keep breaking down until you reach individual controls

### 4. Complex Layout Strategy

**For Complex Layouts:**
1. Try horizontal axis division first
2. If sections get split, try vertical axis
3. Choose the axis that doesn't split any sections
4. Apply recursively to child containers

**When Process Doesn't Work:**
- Use Manual Layout container as root
- Manually position child containers
- **Warning:** Manual layouts are NOT responsive

### 5. Individual Section Layout Rules

**Single Control Sections:**
- Add control directly to container
- Use container alignment properties
- Direction doesn't matter

**Multiple Control Sections:**
- Ask: "Can this be divided into subsections?"
- Apply same wireframe process
- Use container direction and child containers

### 6. Content Grouping Benefits

**First Generation Problems:**
- Had to select controls one by one to copy
- Superficial grouping with no editable properties
- No subgroups within groups
- Manual changes to every control

**Container Solutions:**
- Select parent container to copy entire section
- Copy/paste entire content groups
- Share YAML code with colleagues
- Resize/repurpose entire sections easily

### 7. Control Modification

**Border Radius Technique:**
```yaml
- StyledContainer:
    Control: GroupContainer@1.3.0
    Properties:
      RadiusBottomLeft: =8
      RadiusBottomRight: =8
      RadiusTopLeft: =8
      RadiusTopRight: =8
    Children:
      - StyledControl:
          Control: ComboBox@2.4.0  # Gets border radius from parent
```

**Benefits:**
- Apply border radius to ANY control
- Uniform styling across all controls
- No more boxy first-generation look

### 8. Developer UX Improvements

**Tree View Hierarchy:**
- Structured hierarchy instead of flat list
- Easy to find controls by section
- Logical organization of app components
- Easier maintenance for complex apps

### 9. Gallery Container Pattern

**Gallery Root Container:**
```yaml
- GalleryRootContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      Height: =Parent.TemplateHeight
      Width: =Parent.TemplateWidth
      X: =0
      Y: =0
```

**Custom Gallery Padding:**
```yaml
Properties:
  Width: =Parent.TemplateWidth * 0.9
  Height: =Parent.TemplateHeight * 0.9
  Y: =(Parent.TemplateHeight - Self.Height) / 2  # Vertical center
  X: =0  # Left aligned
```

### 10. AutoHeight Property

**Critical for Responsiveness:**
```yaml
- ResponsiveText:
    Control: Text@0.0.51
    Properties:
      AutoHeight: =true  # Height adjusts based on content
      Text: ="Dynamic content"
```

**Benefits:**
- Text height adjusts to content length
- Essential for responsive design
- Prevents text cutoff on different screen sizes

### 11. Responsive Design Principles

**Key Properties:**
- `LayoutWrap: =true` - Enables wrapping
- `AutoHeight: =true` - Flexible text sizing
- `FillPortions` - Proportional sizing
- `LayoutDirection` - Controls flow direction

**Testing Approach:**
- Start with desktop layout
- Test on tablet (medium screen)
- Test on mobile (small screen)
- Ensure no horizontal scrolling

## Modern UI Design Patterns

### Container Hierarchy Example:
```
Root Container (Vertical)
├── Header Container (Horizontal)
├── Content Container (Horizontal, LayoutWrap=true)
│   ├── Section A Container (Vertical)
│   ├── Section B Container (Vertical)
│   └── Section C Container (Vertical)
└── Footer Container (Horizontal)
```

**Remember:** Containers enable modern, responsive, maintainable Power Apps!# Respon
sive Power Apps - Complete Video 3 Guide

## Three Components of Responsive UI

### 1. Device Screen Size & Aspect Ratio
- Physical screen size and orientation (portrait/landscape)
- Determines available real estate

### 2. Canvas App Code
- All controls and Power FX formulas
- Must be written responsively

### 3. Power Apps Engine
- Takes device info + app code
- Renders final UI based on settings
- **Must be configured correctly**

## Power Apps Engine Configuration

### Essential Settings:
```
App Type: Choose "Tablet" (not Mobile)
Settings > Display:
- Scale to fit: OFF
- Lock orientation: OFF  
- Show mobile notification area: ON (recommended)
```

**Why Tablet App Type:**
- Tablet apps can be responsive for mobile AND desktop
- Mobile apps cannot be made responsive for larger screens

## Screen Size Breakpoints

### Default Power Apps Breakpoints:
- **Size 1 (Mobile)**: < 600px
- **Size 2 (Vertical Tablet)**: 600px - 900px  
- **Size 3 (Horizontal Tablet)**: 900px - 1200px
- **Size 4 (Desktop)**: > 1200px

### Screen Size Variables:
```powerfx
Screen.Size = 1, 2, 3, or 4
ScreenSize.Small = 1
ScreenSize.Medium = 2  
ScreenSize.Large = 3
ScreenSize.ExtraLarge = 4
```

### Custom Breakpoints:
- Fully customizable in App settings
- Recommended: Use Bootstrap breakpoints (576, 768, 992, 1200, 1400)
- ScreenSize variables only go up to ExtraLarge (4)

## Two Golden Rules of Responsive Code

### Rule 1: Relative Sizing
**Every control size should be relative to screen or parent container**

```yaml
# GOOD - Relative sizing
Width: =Parent.Width
Height: =Parent.Height

# BAD - Fixed sizing  
Width: =500
Height: =300
```

### Rule 2: Screen Size Queries
**Use screen sizes and breakpoints to adjust control visibility and properties**

#### Visibility Examples:
```powerfx
# Show only on desktop
Visible: =Screen.Size = 4

# Show only on tablets
Visible: =Screen.Size = 2 Or Screen.Size = 3

# Hide on mobile
Visible: =Screen.Size > 1
```

#### Property Examples:
```powerfx
# Responsive font size
Size: =Switch(Screen.Size, 1, 14, 2, 16, 3, 18, 4, 20)

# Responsive padding
PaddingLeft: =If(Screen.Size <= 2, 10, 20)
```

## Container Layering for Popups

### Base Root Container Pattern:
```yaml
- BaseRootContainer:
    Control: GroupContainer@1.3.0
    Variant: Manual  # Manual for layering
    Properties:
      Height: =Parent.Height
      Width: =Parent.Width
      X: =0
      Y: =0
    Children:
      - MainAppLayer:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
      - PopupLayer:
          Control: GroupContainer@1.3.0
          Variant: Manual
```

## Responsive Menu Patterns

### Three Mobile Menu Types:
1. **Popup Menu**: Hamburger → Side menu appears
2. **Bottom Menu Bar**: All items at bottom
3. **Combination Menu**: Bottom + Popup for less used items

### Popup Menu Implementation:
```yaml
- PopupMenuContainer:
    Properties:
      Height: =Parent.Height
      Width: =Parent.Width * 0.8  # 80% width
      Visible: =MenuExpanded And Screen.Size <= 2
```

### Responsive Menu Logic:
```powerfx
# Side menu visibility
Visible: =Screen.Size >= 3

# Popup menu visibility  
Visible: =MenuExpanded And Screen.Size <= 2

# Static header visibility
Visible: =Screen.Size <= 2
```

## LayoutWrap Magic - The Key to Responsiveness

### How LayoutWrap Works:
- `LayoutWrap: =true` moves items to next line when no space
- **Most important property for responsive design**

### Three Steps for Perfect Wrap:
1. **Set item width**
2. **Set item height** 
3. **Set parent container height**

#### Item Width Formula:
```powerfx
Width: =Switch(
  Screen.Size,
  1, Parent.Width,  # Mobile: full width
  2, (Parent.Width - Parent.PaddingLeft - Parent.PaddingRight - LayoutGap) / 2,  # Tablet: 2 per row
  3, 200,  # Desktop: fixed width
  4, 200
)
```

#### Parent Height Formula:
```powerfx
Height: =Switch(
  Screen.Size,
  1, (ItemHeight * 4) + (LayoutGap * 3) + PaddingTop + PaddingBottom,  # 4 rows
  2, (ItemHeight * 2) + (LayoutGap * 1) + PaddingTop + PaddingBottom,  # 2 rows  
  3, ItemHeight + PaddingTop + PaddingBottom,  # 1 row
  4, ItemHeight + PaddingTop + PaddingBottom
)
```

## Dynamic Height Strategies

### Strategy 1: Static Height Child Items
```powerfx
# Parent height = sum of child heights + gaps + padding
Height: =ChildHeight1 + ChildHeight2 + ChildHeight3 + (LayoutGap * 2) + PaddingTop + PaddingBottom
```

### Strategy 2: Fixed Parent Height
```powerfx
# Set parent height, let children adjust
Height: =Switch(Screen.Size, 1, 300, 2, 250, 3, 200, 4, 200)
```

### Strategy 3: Flexible Height Items
```powerfx
# One child controls parent height, others adjust
# Gallery controls section height:
Gallery.Height: =Self.AllItems.Count * Self.TemplateHeight
Parent.Height: =Gallery.Height + OtherChildrenHeight + Padding
```

## Gallery Responsive Patterns

### Gallery Root Container:
```yaml
- GalleryRootContainer:
    Properties:
      Height: =Parent.TemplateHeight
      Width: =Parent.TemplateWidth
      X: =0
      Y: =0
```

### Responsive Template Size:
```powerfx
TemplateSize: =Switch(
  Screen.Size,
  1, Parent.Width,  # Mobile: 1 column
  2, Parent.Width / 2,  # Tablet: 2 columns
  3, Parent.Width / 3,  # Desktop: 3 columns
  4, Parent.Width / 4
)
```

### Responsive Item Count:
```powerfx
Items: =Switch(
  Screen.Size,
  1, FirstN(DataSource, 5),  # Mobile: 5 items
  2, FirstN(DataSource, 8),  # Tablet: 8 items  
  3, FirstN(DataSource, 12), # Desktop: 12 items
  4, FirstN(DataSource, 16)
)
```

## Form Responsiveness

### Form Control Benefits:
- **Responsive by default**
- Data cards stretch automatically
- Controls positioned relative to each other

### Making Forms More Responsive:
1. **Turn on Width Fits** for each data card
2. **Set data card widths** in form properties
3. **Use responsive width formulas**:
```powerfx
DataCard.Width: =Switch(
  Screen.Size,
  1, Parent.Width,  # Mobile: full width
  2, Parent.Width / 2,  # Tablet: half width
  3, Parent.Width / 3,  # Desktop: third width
  4, Parent.Width / 3
)
```

## Best Practices

### Development Tips:
1. **Add screen size label** during development for testing
2. **Save before cutting/pasting** containers (avoid losing work)
3. **Test on all breakpoints** regularly
4. **Focus on target devices** - ask client which devices matter most

### Performance Considerations:
- Don't make every control query screen size (slow)
- Use container-level responsive logic when possible
- Minimize complex formulas in frequently updated properties

### UX Guidelines:
- **App doesn't need to be perfect on every screen size**
- **Must be functional and usable** on all target devices
- **Ask clients about target devices** to prioritize effort
- **Small hiccups okay, broken functionality not okay**

## Testing Checklist

✅ **Desktop (Size 4)**: Full layout with all features
✅ **Horizontal Tablet (Size 3)**: Slightly condensed but functional  
✅ **Vertical Tablet (Size 2)**: Wrapped layout, some items hidden
✅ **Mobile (Size 1)**: Stacked layout, popup menus, essential features only

**Remember: LayoutWrap + Screen Size queries = Responsive Power Apps mastery!**# New Co
ntainer Properties & Responsive Insights

## Scroll Properties (CONFIRMED WORKING)

### LayoutOverflow Properties:
```yaml
- Container:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      LayoutOverflowX: =LayoutOverflow.Scroll  # Horizontal scroll
      LayoutOverflowY: =LayoutOverflow.Scroll  # Vertical scroll
```

**Key Discovery:** Scroll properties work on some containers but not others - needs testing per container level.

## Text Width Requirements

### Critical Finding: Text Controls Need Width for Long Content
```yaml
- LongTextControl:
    Control: Text@0.0.51
    Properties:
      Text: ="Long text content needs explicit width"
      Width: =200  # REQUIRED for longer text content
```

**Rule:** The more text content, the more explicit width is needed for proper display.

## Responsive Scroll Strategy

### When LayoutWrap is Used:
- **Problem**: Wrapped content may be cut off without scroll
- **Solution**: Add scroll properties to parent containers
- **Best Practice**: Test scroll on each container level

### Container Hierarchy for Scroll:
```yaml
- OuterContainer:
    Properties:
      LayoutOverflowX: =LayoutOverflow.Scroll  # May work
      LayoutOverflowY: =LayoutOverflow.Scroll
    Children:
      - InnerContainer:
          Properties:
            LayoutWrap: =true  # Content wraps
            # Scroll may not work at this level
```

## Improved Responsive Pattern

### Container-within-Container Strategy:
1. **Outer Container**: Handles scroll and overall layout
2. **Inner Container**: Handles wrapping and content organization
3. **Content Containers**: Handle individual sections

### Example Structure:
```yaml
- ScrollableContainer:
    Properties:
      LayoutOverflowX: =LayoutOverflow.Scroll
      LayoutOverflowY: =LayoutOverflow.Scroll
    Children:
      - WrapContainer:
          Properties:
            LayoutWrap: =true
            LayoutDirection: =LayoutDirection.Horizontal
          Children:
            - ContentSection1: {}
            - ContentSection2: {}
```

## Text Width Guidelines

### Width Requirements by Content Length:
- **Short text** (< 20 chars): Width optional
- **Medium text** (20-50 chars): Width: =150-200
- **Long text** (> 50 chars): Width: =200-300
- **Very long text**: Width: =300+ or use AutoHeight

### Responsive Text Width:
```yaml
Width: =Switch(
  Screen.Size,
  1, 200,  # Mobile: smaller width
  2, 250,  # Tablet: medium width
  3, 300,  # Large: full width
  4, 350
)
```

## Scroll Troubleshooting

### Why Scroll May Not Work:
1. **Container Level**: Scroll works better on outer containers
2. **Content Size**: Container must have defined height/width
3. **Hierarchy**: Inner containers may not inherit scroll properly
4. **LayoutWrap Conflict**: Wrap + Scroll may conflict at same level

### Solutions:
1. **Move scroll to parent container**
2. **Use container-within-container pattern**
3. **Set explicit dimensions on scrollable container**
4. **Test scroll at different hierarchy levels**

## Updated Responsive Best Practices

### 1. Container Hierarchy:
```
ScrollContainer (with LayoutOverflow)
└── WrapContainer (with LayoutWrap)
    ├── Section1Container
    ├── Section2Container
    └── Section3Container
```

### 2. Text Width Strategy:
- Always set Width for text with dynamic/long content
- Use responsive width formulas for different screen sizes
- Test text display across all breakpoints

### 3. Scroll Implementation:
- Add scroll to outermost containers first
- Test scroll functionality at each level
- Use both X and Y scroll for maximum flexibility

**Key Insight:** Responsive design requires both wrapping AND scrolling - wrap for layout, scroll for overflow content!

## Responsive Header Pattern (3 breakpoints)

Use this pattern to keep a header working on mobile (Size 1), tablet (Size 2-3) and desktop (Size 4): back button on the left, title block centered (Name over Subtitle), and a right-aligned badge/label. The header height is dynamic on mobile to prevent clipping when items wrap.

### Rules
- Layout: Horizontal, `LayoutWrap=true`, `LayoutJustifyContent=SpaceBetween`, small `LayoutGap`.
- Title block: Vertical container, `LayoutWrap=false`, `LayoutAlignItems=Stretch`, always stacks Subtitle under Name (all sizes).
- Min widths: Set `LayoutMinWidth` for each child using breakpoints to control wrapping.
- Height: Sum of row heights on Size 1; otherwise max row height.

### YAML Snippet
```yaml
- ResponsiveHeader:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      FillPortions: =0
      LayoutDirection: =LayoutDirection.Horizontal
      LayoutWrap: =true
      LayoutGap: =16
      LayoutAlignItems: =LayoutAlignItems.Center
      LayoutJustifyContent: =LayoutJustifyContent.SpaceBetween
      PaddingTop: =8
      PaddingBottom: =8
      PaddingLeft: =8
      PaddingRight: =8
      Height: |
        =If(
          Screen.Size = 1,
          BackBtn.Height + TitleBlock.Height + RightBadge.Height + (Self.LayoutGap * 2) + Self.PaddingTop + Self.PaddingBottom,
          Max(BackBtn.Height, TitleBlock.Height, RightBadge.Height) + Self.PaddingTop + Self.PaddingBottom
        )
    Children:
      - BackBtn:
          Control: Button@0.0.45
          Properties:
            Height: =32
            Icon: ="ArrowLeft"
            Layout: ='ButtonCanvas.Layout'.IconBeforeText
            Text: ="Back"
            LayoutMinWidth: |
              =If(Screen.Size >= 3, 120, Screen.Size = 2, 140, Parent.Width - Parent.PaddingLeft - Parent.PaddingRight)
      - TitleBlock:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            FillPortions: =1
            LayoutDirection: =LayoutDirection.Vertical
            LayoutAlignItems: =LayoutAlignItems.Stretch
            LayoutWrap: =false
            LayoutGap: =2
            PaddingLeft: =10
            Height: =If(Screen.Size <= 2, 80, 64)
            LayoutMinWidth: |
              =If(Screen.Size >= 3, 260, Screen.Size = 2, 300, Parent.Width - Parent.PaddingLeft - Parent.PaddingRight)
          Children:
            - Title:
                Control: Label@2.5.1
                Properties:
                  AutoHeight: =true
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Bold
                  Size: =15
                  Text: ="[Name]"
                  Width: =Parent.Width
            - Subtitle:
                Control: Label@2.5.1
                Properties:
                  AutoHeight: =true
                  Font: =Font.'Open Sans'
                  Text: ="[Subtitle]"
                  Width: =Parent.Width
      - RightBadge:
          Control: Label@2.5.1
          Properties:
            Color: =RGBA(255, 0, 0, 1)
            DisplayMode: =DisplayMode.View
            Size: =10
            Text: ="[badge]"
            LayoutMinWidth: |
              =If(Screen.Size >= 3, 160, Screen.Size = 2, 180, Parent.Width - Parent.PaddingLeft - Parent.PaddingRight)
```

### When to use
- Headers that must keep the back button and a status badge visible on mobile while stacking the title lines.
- Works with Power Apps default breakpoints (Size 1..4). Replace `Screen` with the actual screen variable if needed.