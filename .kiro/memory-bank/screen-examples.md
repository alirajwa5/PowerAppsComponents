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

## Training Dashboard Header Example (All Breakpoints)

```yaml
Screens:
  srcTrainingDashboard:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - Container1:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            Height: =Parent.Height
            LayoutDirection: =LayoutDirection.Vertical
            LayoutGap: =16
            PaddingBottom: =16
            PaddingLeft: =16
            PaddingRight: =16
            PaddingTop: =16
            Width: =Parent.Width
          Children:
            - srcTrainingHeaderContainer:
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
                      srcTrainingDashboard.Size = 1,
                      ButtonCanvas2.Height + ContainerTitle.Height + LabelTraining.Height + (Self.LayoutGap * 2) + Self.PaddingTop + Self.PaddingBottom,
                      Max(ButtonCanvas2.Height, ContainerTitle.Height, LabelTraining.Height) + Self.PaddingTop + Self.PaddingBottom
                    )
                Children:
                  - ButtonCanvas2:
                      Control: Button@0.0.45
                      Properties:
                        Height: =32
                        Icon: ="ArrowLeft"
                        Layout: ='ButtonCanvas.Layout'.IconBeforeText
                        Text: ="Back"
                        LayoutMinWidth: |
                          =If(srcTrainingDashboard.Size >= 3, 120, srcTrainingDashboard.Size = 2, 140, Parent.Width - Parent.PaddingLeft - Parent.PaddingRight)
                  - ContainerTitle:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        FillPortions: =1
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutAlignItems: =LayoutAlignItems.Stretch
                        LayoutWrap: =false
                        LayoutGap: =2
                        PaddingLeft: =10
                        Height: =If(srcTrainingDashboard.Size <= 2, 80, 64)
                      Children:
                        - LabelName:
                            Control: Label@2.5.1
                            Properties:
                              AutoHeight: =true
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Size: =15
                              Text: ="David Wilson"
                        - LabelSubtitle:
                            Control: Label@2.5.1
                            Properties:
                              AutoHeight: =true
                              Font: =Font.'Open Sans'
                              Text: ="Applicant Profile"
                  - LabelTraining:
                      Control: Label@2.5.1
                      Properties:
                        Color: =RGBA(255, 0, 0, 1)
                        DisplayMode: =DisplayMode.View
                        Size: =10
                        Text: ="training review"
```