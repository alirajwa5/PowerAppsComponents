# Button Component Definitions

## Component Structure
```yaml
ComponentDefinitions:
  Buttons:
    DefinitionType: CanvasComponent
    Children:
```

## Primary Button
```yaml
- PrimaryButton:
    Control: Classic/Button@2.2.0
    Properties:
      BorderColor: =ColorFade(Self.Fill, -15%)
      Color: =RGBA(255, 255, 255, 1)
      DisabledBorderColor: =RGBA(166, 166, 166, 1)
      Fill: =RGBA(56, 96, 178, 1)
      Font: =Font.'Open Sans'
      Height: =41
      HoverBorderColor: =ColorFade(Self.BorderColor, 20%)
      HoverColor: =RGBA(255, 255, 255, 1)
      HoverFill: =ColorFade(RGBA(56, 96, 178, 1), -20%)
      PressedBorderColor: =Self.Fill
      PressedColor: =Self.Fill
      PressedFill: =Self.Color
      Text: ="Button Text"
      Width: =200
```

## Secondary Button
```yaml
- SecondaryButton:
    Control: Classic/Button@2.2.0
    Properties:
      BorderColor: =RGBA(0, 0, 0, 0)
      BorderStyle: =BorderStyle.None
      Color: =RGBA(255, 255, 255, 1)
      DisabledBorderColor: =RGBA(0, 0, 0, 0)
      DisabledColor: =RGBA(161, 159, 157, 1)
      DisabledFill: =RGBA(242, 242, 241, 0)
      Fill: =RGBA(0, 120, 212, 1)
      Font: =Font.'Segoe UI'
      HoverBorderColor: =RGBA(0, 0, 0, 0)
      HoverColor: =RGBA(255, 255, 255, 1)
      HoverFill: =RGBA(16, 110, 190, 1)
      PressedBorderColor: =RGBA(0, 69, 120, 1)
      PressedColor: =RGBA(255, 255, 255, 1)
      PressedFill: =RGBA(16, 110, 190, 1)
      RadiusBottomLeft: =0
      RadiusBottomRight: =0
      RadiusTopLeft: =0
      RadiusTopRight: =0
      Text: ="Button Text"
```

## Modern Button
```yaml
- ModernButton:
    Control: Button@0.0.45
    Properties:
      AccessibleLabel: ="Button description"
      Text: ="Button Text"
      Width: =140
```

## Button Variants Summary
- **PrimaryButton**: Blue gradient with ColorFade effects, Open Sans font
- **SecondaryButton**: Standard Power Apps blue, Segoe UI font, no radius
- **ModernButton**: Simplified modern control with minimal properties