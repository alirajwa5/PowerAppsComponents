# Login Screen (srcLogin)

## Overview
Login screen with email/password authentication, validation, and role-based navigation.

## Features
- Email and password validation with visual error states
- Role-based navigation (Admin vs Agent)
- Centered login form with company branding
- Real-time validation feedback

## Screen Code
```yaml
Screens:
  scrLogin:
    Properties:
      Fill: =RGBA(228, 228, 228, 1)
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
      OnVisible: |
        =Set(varEmailEmptyError, false);
        Set(varPasswordEmptyError, false);
        Set(varInvalidLogin,false)
    Children:
      - LoginContainer:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(228, 228, 228, 1)
            Fill: =RGBA(228, 228, 228, 1)
            Height: =450
            Width: =400
            X: =(Parent.Width - Self.Width) / 2
            Y: =(Parent.Height - Self.Height) / 2
      - TitleLabel:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(33, 56, 194, 1)
            Font: =Font.'Open Sans'
            FontWeight: =FontWeight.Bold
            Height: =34
            Size: =15
            Text: ="Applicant Onboarding System"
            Width: =360
            Wrap: =false
            X: =(Parent.Width - Self.Width) / 2
            Y: =LoginContainer.Y + 30
      - SubtitleLabel:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(50, 49, 48, 1)
            DisabledColor: =RGBA(40, 40, 40, 1)
            Font: =Font.'Open Sans'
            Height: =27
            Text: ="Please sign in to continue"
            Width: =360
            X: =(Parent.Width - Self.Width) / 2
            Y: =TitleLabel.Y + TitleLabel.Height + 10
      - InvalidLoginLabel:
          Control: Label@2.5.1
          Properties:
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(255, 0, 0, 1)
            Font: =Font.'Open Sans'
            Height: =34
            Size: =10
            Text: ="Invalid credentials"
            Visible: =varInvalidLogin
            Width: =360
            Wrap: =false
            X: =PasswordInput.X
            Y: |
              =PasswordInput.Y + PasswordInput.Height + 3
      - EmailLabel:
          Control: Label@2.5.1
          Properties:
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(40, 40, 40, 1)
            Font: =Font.'Open Sans'
            Height: =34
            Text: ="Email *"
            Width: =360
            Wrap: =false
            X: =(Parent.Width - Self.Width) / 2
            Y: =SubtitleLabel.Y + SubtitleLabel.Height + 25
      - EmailInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: |
              =If(varEmailEmptyError && Len(Trim(Self.Text)) = 0,
                Color.Red,
                RGBA(33, 56, 194, 1))
            Default: =""
            FocusedBorderColor: =RGBA(33, 56, 194, 1)
            Font: =Font.'Open Sans'
            HintText: ="Enter your email"
            OnChange: |
              =Set(varEmailEmptyError, false);
              Set(varInvalidLogin, false)
            OnSelect: =Set(varEmailEmptyError, false)
            Width: =360
            X: =(Parent.Width - Self.Width) / 2
            Y: =EmailLabel.Y + EmailLabel.Height + 5
      - PasswordLabel:
          Control: Label@2.5.1
          Properties:
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(40, 40, 40, 1)
            Font: =Font.'Open Sans'
            Height: =34
            Text: ="Password *"
            Width: =360
            Wrap: =false
            X: =(Parent.Width - Self.Width) / 2
            Y: =EmailInput.Y + EmailInput.Height + 20
      - PasswordInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: |
              =If(varPasswordEmptyError && Len(Trim(Self.Text)) = 0,
                Color.Red,
                RGBA(33, 56, 194, 1))
            Default: =""
            FocusedBorderColor: =RGBA(33, 56, 194, 1)
            Font: =Font.'Open Sans'
            HintText: ="Enter your password"
            Mode: =TextMode.Password
            OnChange: |
              =Set(varPasswordEmptyError, false);
              Set(varInvalidLogin, false)
            OnSelect: |
              =Set(varPasswordEmptyError, false);
            Width: =360
            X: =(Parent.Width - Self.Width) / 2
            Y: =PasswordLabel.Y + PasswordLabel.Height + 5
      - LoginButton:
          Control: Classic/Button@2.2.0
          Properties:
            BorderColor: =RGBA(33, 56, 194, 1)
            Color: =RGBA(0, 0, 0, 1)
            DisabledBorderColor: =RGBA(166, 166, 166, 1)
            Fill: =RGBA(191, 184, 152, 1)
            Font: =Font.'Open Sans'
            Height: =41
            HoverBorderColor: =ColorFade(Self.BorderColor, 20%)
            HoverColor: =RGBA(255, 255, 255, 1)
            HoverFill: =ColorFade(RGBA(56, 96, 178, 1), -20%)
            OnSelect: |
              =// Clear previous state
              Set(varInvalidLogin, false);
              
              // Check for empty fields first
              Set(varEmailEmptyError, Len(Trim(EmailInput.Text)) = 0);
              Set(varPasswordEmptyError, Len(Trim(PasswordInput.Text)) = 0);
              
              If(varEmailEmptyError || varPasswordEmptyError,
                // Stop here — at least one field is empty
                Blank(),
                // Admin credentials
                Lower(Trim(EmailInput.Text)) = "admin@company.com" && Trim(PasswordInput.Text) = "123",
                Navigate(srcAdminDashboardoverview, ScreenTransition.Fade),
                // Agent credentials
                Lower(Trim(EmailInput.Text)) = "agent@company.com" && Trim(PasswordInput.Text) = "123",
                Navigate(srcServicingAgentDashboard, ScreenTransition.Fade),
                // Else — credentials don't match
                Set(varInvalidLogin, true)
              )
            PressedBorderColor: =Self.Fill
            PressedColor: =Self.Fill
            PressedFill: =Self.Color
            Text: ="Sign In"
            Width: =360
            X: =(Parent.Width - Self.Width) / 2
            Y: =PasswordInput.Y + PasswordInput.Height + 30
      - Image1:
          Control: Image@2.2.3
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Image: ='Logo jonbesh'
            X: =633
            Y: =89
```

## Key Patterns
- **Centered Layout**: Uses `(Parent.Width - Self.Width) / 2` for horizontal centering
- **Validation Logic**: Real-time border color changes based on validation state
- **Role-Based Navigation**: Different screens for admin vs agent roles
- **State Management**: Uses variables for error states and validation
- **Responsive Positioning**: Elements positioned relative to each other using Y calculations

## Variables Used
- `varEmailEmptyError`: Boolean for email validation
- `varPasswordEmptyError`: Boolean for password validation  
- `varInvalidLogin`: Boolean for invalid credentials

## Navigation Targets
- Admin: `srcAdminDashboardoverview`
- Agent: `srcServicingAgentDashboard`

## Credentials
- Admin: admin@company.com / 123
- Agent: agent@company.com / 123