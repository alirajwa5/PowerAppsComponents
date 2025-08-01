# Power Apps Component Patterns

## Button Pattern
```yaml
Control: Classic/Button@2.2.0
Properties:
  BorderColor: =RGBA(0, 0, 0, 0)
  BorderStyle: =BorderStyle.None
  Color: =RGBA(255, 255, 255, 1)
  Fill: =RGBA(0, 120, 212, 1)
  Font: =Font.'Segoe UI'
  HoverColor: =RGBA(255, 255, 255, 1)
  HoverFill: =RGBA(16, 110, 190, 1)
  OnSelect: =Action()
  PressedColor: =RGBA(255, 255, 255, 1)
  PressedFill: =RGBA(16, 110, 190, 1)
  Text: ="Button Text"
```

## Icon Button Pattern
```yaml
Control: Classic/Icon@2.5.0
Properties:
  BorderColor: =RGBA(0, 0, 0, 0)
  Color: =RGBA(0, 120, 212, 1)
  FocusedBorderThickness: =4
  Height: =50
  HoverColor: =RGBA(16, 110, 190, 1)
  Icon: =Icon.Add
  OnSelect: =Action()
  PaddingBottom: =12
  PaddingLeft: =12
  PaddingRight: =12
  PaddingTop: =12
  PressedColor: =RGBA(16, 110, 190, 1)
  Width: =50
```

## Text Input Pattern
```yaml
Control: Classic/TextInput@2.3.2
Properties:
  BorderColor: =RGBA(0, 0, 0, 1)
  Color: =RGBA(50, 49, 48, 1)
  Font: =Font.'Segoe UI'
  HoverBorderColor: =RGBA(16, 110, 190, 1)
  PaddingLeft: =5
  PressedBorderColor: =RGBA(0, 120, 212, 1)
  Size: =14
```

## Container Pattern
```yaml
Control: GroupContainer@1.3.0
Variant: AutoLayout
Properties:
  LayoutDirection: =LayoutDirection.Vertical
  LayoutGap: =15
  PaddingBottom: =16
  PaddingLeft: =16
  PaddingRight: =16
  PaddingTop: =16
```

## Label Pattern
```yaml
Control: Label@2.5.1
Properties:
  Color: =RGBA(50, 49, 48, 1)
  Font: =Font.'Segoe UI'
  FontWeight: =FontWeight.Semibold
  Size: =14
  Text: ="Label Text"
```