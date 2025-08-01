# Screen Examples

## Login Screen Structure

### Screen Properties
```yaml
Screens:
  scrLogin:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
```

### Component Layout
```yaml
- LoginContainer:
    Control: Rectangle@2.3.0
    Properties:
      BorderColor: =RGBA(0, 18, 107, 1)
      Fill: =RGBA(255, 255, 255, 1)
      Height: =450
      Width: =400
      X: =(Parent.Width - Self.Width) / 2
      Y: =(Parent.Height - Self.Height) / 2

- TitleLabel:
    Control: Label@2.5.1
    Properties:
      Align: =Align.Center
      AutoHeight: =true
      Color: =RGBA(0, 18, 107, 1)
      Font: =Font.'Open Sans'
      FontWeight: =FontWeight.Bold
      Size: =15
      Text: ="Applicant Onboarding System"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =LoginContainer.Y + 30

- SubtitleLabel:
    Control: Label@2.5.1
    Properties:
      AutoHeight: =true
      Color: =RGBA(50, 49, 48, 1)
      Font: =Font.'Open Sans'
      Text: ="Please sign in to continue"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =TitleLabel.Y + TitleLabel.Height + 10

- EmailLabel:
    Control: Label@2.5.1
    Properties:
      AutoHeight: =true
      Color: =RGBA(0, 18, 107, 1)
      Font: =Font.'Open Sans'
      Text: ="Email *"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =SubtitleLabel.Y + SubtitleLabel.Height + 25

- EmailInput:
    Control: Classic/TextInput@2.3.2
    Properties:
      BorderColor: =RGBA(0, 18, 107, 1)
      Font: =Font.'Open Sans'
      HintText: ="Enter your email"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =EmailLabel.Y + EmailLabel.Height + 5

- PasswordLabel:
    Control: Label@2.5.1
    Properties:
      AutoHeight: =true
      Color: =RGBA(0, 18, 107, 1)
      Font: =Font.'Open Sans'
      Text: ="Password *"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =EmailInput.Y + EmailInput.Height + 20

- PasswordInput:
    Control: Classic/TextInput@2.3.2
    Properties:
      BorderColor: =RGBA(0, 18, 107, 1)
      Font: =Font.'Open Sans'
      HintText: ="Enter your password"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =PasswordLabel.Y + PasswordLabel.Height + 5

- LoginButton:
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
      Text: ="Sign In"
      Width: =360
      X: =(Parent.Width - Self.Width) / 2
      Y: =PasswordInput.Y + PasswordInput.Height + 30
```

## Key Patterns from Login Screen

### Centering Formula
- **Horizontal**: `X: =(Parent.Width - Self.Width) / 2`
- **Vertical**: `Y: =(Parent.Height - Self.Height) / 2`

### Positioning Chain
- Elements positioned relative to previous element: `Y: =PreviousElement.Y + PreviousElement.Height + spacing`

### Color Scheme
- **Primary Dark Blue**: RGBA(0, 18, 107, 1)
- **Primary Blue**: RGBA(56, 96, 178, 1)
- **Text Gray**: RGBA(50, 49, 48, 1)
- **White Background**: RGBA(255, 255, 255, 1)

### Form Structure
1. Container (Rectangle)
2. Title + Subtitle
3. Label + Input pairs
4. Action button