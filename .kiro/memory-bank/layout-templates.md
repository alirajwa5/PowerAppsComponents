# Layout Templates

## Split Screen Template

### Overview
A horizontal split screen layout with two equal containers side by side. Perfect for master-detail views, comparison screens, or dual-panel interfaces.

### Structure
```yaml
Screens:
  SplitScreen:
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
            LayoutDirection: =LayoutDirection.Horizontal
            LayoutGap: =16
            LayoutWrap: =true
            PaddingBottom: =16
            PaddingLeft: =16
            PaddingRight: =16
            PaddingTop: =16
            Width: =Parent.Width
          Children:
            - LeftContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  Fill: =RGBA(255, 255, 255, 1)
                  LayoutDirection: =LayoutDirection.Vertical
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
            - RightContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  Fill: =RGBA(255, 255, 255, 1)
                  LayoutDirection: =LayoutDirection.Vertical
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
```

### Use Cases
- Master-Detail views, Comparison screens, Form sections, Dashboard panels

## Sidebar Layout Template

### Overview
A classic sidebar layout with header, sidebar navigation, and main content area. The sidebar takes 30% width (FillPortions=3) and main content takes 70% (FillPortions=7).

### Structure
```yaml
Screens:
  SidebarScreen:
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
          Children:
            - HeaderContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  Fill: =RGBA(255, 255, 255, 1)
                  FillPortions: =0
                  Height: =75
                  LayoutDirection: =LayoutDirection.Horizontal
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
            - BottomContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  Fill: =RGBA(245, 245, 245, 1)
                  LayoutAlignItems: =LayoutAlignItems.Stretch
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutGap: =16
                  LayoutWrap: =true
                  PaddingBottom: =2
                  PaddingLeft: =2
                  PaddingRight: =2
                  PaddingTop: =2
                Children:
                  - SidebarContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 255, 255, 1)
                        FillPortions: =3
                        LayoutDirection: =LayoutDirection.Vertical
                        RadiusBottomLeft: =8
                        RadiusBottomRight: =8
                        RadiusTopLeft: =8
                        RadiusTopRight: =8
                  - MainContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 255, 255, 1)
                        FillPortions: =7
                        LayoutDirection: =LayoutDirection.Vertical
                        RadiusBottomLeft: =8
                        RadiusBottomRight: =8
                        RadiusTopLeft: =8
                        RadiusTopRight: =8
```

### Use Cases
- Admin dashboards, Settings pages, File browsers, Documentation sites

## Header and Footer Template

### Overview
A classic header and footer layout where the "footer" is actually the main content area containing sidebar and main sections.

### Key Features
- Fixed header with FillPortions=0 and Height=75
- BottomContainer serves as the main content area
- Nested sidebar+main layout within the "footer" area
- Standard Power Apps pattern for application shells

### Use Cases
- Application shells, Navigation layouts, Dashboard layouts, Multi-section apps