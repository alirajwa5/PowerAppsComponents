# Power Apps Screen Structure Patterns

## Modern Screen Architecture

### Basic Screen Structure
```yaml
Screens:
  ScreenName:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - ScreenContainer:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            Fill: =RGBA(245, 245, 245, 1)
            Height: =Parent.Height
            LayoutAlignItems: =LayoutAlignItems.Stretch
            LayoutDirection: =LayoutDirection.Vertical
            LayoutGap: =16
            PaddingBottom: =16
            PaddingLeft: =16
            PaddingRight: =16
            PaddingTop: =16
            Width: =Parent.Width
```

## Container Patterns

### Header Container
```yaml
- HeaderContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      Fill: =RGBA(255, 255, 255, 1)
      FillPortions: =0
      Height: =75
      LayoutDirection: =LayoutDirection.Horizontal
      LayoutAlignItems: =LayoutAlignItems.Center
      RadiusBottomLeft: =8
      RadiusBottomRight: =8
      RadiusTopLeft: =8
      RadiusTopRight: =8
      DropShadow: =DropShadow.Light
    Children:
      - Header:
          Control: Header@0.0.44
          Properties:
            Title: ="Screen Title"
```

### Main Content Container
```yaml
- MainContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      Fill: =RGBA(255, 255, 255, 1)
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      RadiusBottomLeft: =8
      RadiusBottomRight: =8
      RadiusTopLeft: =8
      RadiusTopRight: =8
      DropShadow: =DropShadow.Light
```

## Modern Table Control

### Table Structure
```yaml
- DataTable:
    Control: Table@1.0.278
    Properties:
      Items: =DataSource
      FillPortions: =1
      ReflowBehavior: ='PowerAppsOneGrid.ReflowBehavior'.Reflow
    Children:
      - FieldName:
          Control: TableDataField@1.5.0
          Variant: textualColumn
          IsLocked: true
          Properties:
            FieldDisplayName: ="Display Name"
            FieldName: ="field_name"
            FieldType: ="s"  # s=string, d=date, l=lookup, n=number
            Order: =1
```

## Layout Properties

### GroupContainer AutoLayout Properties
- **LayoutDirection**: Vertical, Horizontal
- **LayoutAlignItems**: Stretch, Center, Start, End
- **LayoutJustifyContent**: Start, Center, End, SpaceBetween
- **LayoutGap**: Spacing between child elements
- **LayoutWrap**: true/false for wrapping
- **FillPortions**: 0=fixed size, 1+=flexible sizing

### Common Styling
- **Fill**: Background color
- **RadiusBottomLeft/Right/TopLeft/Right**: Corner radius (usually 8)
- **DropShadow**: None, Light, Regular, Strong
- **PaddingTop/Bottom/Left/Right**: Internal spacing (usually 16-20)

## Field Types in TableDataField
- **"s"**: String/Text fields
- **"d"**: Date fields  
- **"l"**: Lookup/Choice fields
- **"n"**: Number fields
- **"b"**: Boolean fields

## Best Practices

### Container Hierarchy
1. **ScreenContainer**: Main wrapper with vertical layout
2. **HeaderContainer**: Fixed height header with horizontal layout
3. **MainContainer**: Flexible content area
4. **ActionContainer**: Fixed height footer for buttons

### Responsive Design
- Use **FillPortions** for flexible sizing
- Use **LayoutAlignItems.Stretch** for full width
- Set **Height=Parent.Height** and **Width=Parent.Width** on screen container

### Visual Consistency
- **Background**: Light gray (245, 245, 245) for screen, white for containers
- **Radius**: 8px for all containers
- **Shadows**: Light shadows for subtle elevation
- **Gaps**: 16px standard spacing between containers