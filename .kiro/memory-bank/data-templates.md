# Data Display Templates

## Header and Gallery Template

### Overview
A responsive gallery layout with header and card-based content display. Features responsive grid that adapts from 3 columns (ExtraLarge) to 2 columns (Large) to 1 column (Small screens).

### Key Features
- Responsive grid with WrapCount for 3/2/1 column layout
- Card structure with Image + Title + Description + Button
- Dynamic sizing based on screen size breakpoints
- Modern Gallery@2.15.0 with Vertical variant

### Use Cases
- Product catalogs, Content galleries, Dashboard cards, Portfolio displays, News feeds

## Header + Body with Responsive Header (Reference)

```yaml
Screens:
  ExampleHeaderBody:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - ScreenContainer:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            Height: =Parent.Height
            Width: =Parent.Width
            LayoutDirection: =LayoutDirection.Vertical
            LayoutGap: =16
            PaddingTop: =16
            PaddingBottom: =16
            PaddingLeft: =16
            PaddingRight: =16
          Children:
            - HeaderResponsive: { /* see containers-responsive.md Responsive Header Pattern */ }
            - Main: { Control: GroupContainer@1.3.0, Variant: AutoLayout, Properties: { FillPortions: =1, LayoutDirection: =LayoutDirection.Vertical } }
```

## Header and Table Template

### Overview
A clean data display layout with header and modern Table control. Perfect for displaying tabular data with responsive behavior and professional styling.

### Key Features
- Modern Table@1.0.278 control with responsive behavior
- ReflowBehavior.Reflow for automatic column adaptation
- FillPortions=1 for table to take all available space
- Fixed header with flexible table content

### Use Cases
- Data dashboards, Admin panels, Reports, Inventory systems, CRM systems

## List Template

### Overview
A classic mobile-style list layout with fixed header and gallery using BrowseLayout variant. Features image thumbnails, title/subtitle text, and selection indicators with chevron navigation.

### Key Features
- BrowseLayout_Vertical_TwoTextOneImageVariant_ver5.0 for classic list layout
- Image + Title + Subtitle + Arrow structure
- Selection indicators with blue bar and bold text
- Calculated positioning for proper alignment

### Structure
```yaml
- ItemGallery:
    Control: Gallery@2.15.0
    Variant: BrowseLayout_Vertical_TwoTextOneImageVariant_ver5.0
    Properties:
      BorderColor: =RGBA(0, 18, 107, 1)
      Height: =Parent.Height - Self.Y
      Items: =Applicant
      Width: =Parent.Width
      Y: =64
    Children:
      - ItemImage:
          Control: Image@2.2.3
          Properties:
            Height: =72
            Width: =72
            RadiusBottomLeft: =8
            RadiusBottomRight: =8
            RadiusTopLeft: =8
            RadiusTopRight: =8
            X: =16
            Y: =(Parent.TemplateHeight / 2) - (Self.Height / 2)
      - ItemTitle:
          Control: Label@2.5.1
          Properties:
            FontWeight: =If(ThisItem.IsSelected, FontWeight.Semibold, FontWeight.Normal)
            Size: =14
            Text: =ThisItem.SampleHeading
            Width: =Parent.TemplateWidth - 173
            X: =103
      - NavigationArrow:
          Control: Classic/Icon@2.5.0
          Properties:
            Icon: =Icon.ChevronRight
            Width: =50
            Height: =50
            X: =Parent.TemplateWidth - Self.Width - 12
      - SelectionIndicator:
          Control: Rectangle@2.3.0
          Properties:
            Fill: =RGBA(0, 18, 107, 1)
            Width: =4
            Visible: =ThisItem.IsSelected
```

### Use Cases
- Contact lists, Product catalogs, News feeds, File browsers, Social media, Settings menus