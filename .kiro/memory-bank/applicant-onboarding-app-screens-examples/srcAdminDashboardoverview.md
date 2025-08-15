# Admin Dashboard Overview (srcAdminDashboardoverview)

## Overview
Main admin dashboard with navigation tabs and application statistics overview.

## Features
- Header with title, description, and logout button
- Horizontal navigation tabs (Overview, All Applicants, Reports)
- Statistics cards showing application counts by status
- Clean card-based layout with icons and metrics

## Screen Code
```yaml
Screens:
  srcAdminDashboardoverview:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - Container1_1:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            BorderColor: =RGBA(0, 0, 0, 0)
            DropShadow: =DropShadow.None
            Fill: =RGBA(228, 228, 228, 1)
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
            - Container5:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  BorderColor: =RGBA(214, 221, 224, 1)
                  DropShadow: =DropShadow.None
                  FillPortions: =0
                  Height: =95
                  LayoutDirection: =LayoutDirection.Horizontal
                  Width: =Parent.Width
                Children:
                  - Container29:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        Height: =Parent.Height
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =95
                      Children:
                        - Label1:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(33, 56, 194, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Size: =14
                              Text: ="Admin Dashboard"
                              Width: =Parent.Width
                        - Label2:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(40, 40, 40, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Manage all users and application records • Logged in as System Administrator"
                              Width: =Parent.Width
                  - Container30:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.End
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        LayoutMinHeight: =95
                        PaddingRight: =5
                      Children:
                        - ButtonCanvas7:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              BasePaletteColor: =RGBA(191, 184, 152, 1)
                              BorderColor: =RGBA(33, 56, 194, 1)
                              FontColor: =RGBA(0, 0, 0, 1)
                              Icon: ="ArrowExit"
                              OnSelect: |
                                =Reset(EmailInput);
                                Reset(PasswordInput);
                                // Clear validation & error flags
                                Set(varEmailEmptyError, false);
                                Set(varPasswordEmptyError, false);
                                Set(varInvalidLogin, false);
                                // Navigate back to Login screen
                                Navigate(scrLogin, ScreenTransition.Fade)
                              Text: ="Logout"
            - Container8:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  BorderColor: =RGBA(0, 0, 0, 0)
                  DropShadow: =DropShadow.Semilight
                  FillPortions: =0
                  Height: =70
                  LayoutAlignItems: =LayoutAlignItems.End
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutWrap: =true
                  Width: =Parent.Width
                Children:
                  - Container9:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        AlignInContainer: =AlignInContainer.SetByContainer
                        BorderColor: =RGBA(255, 0, 0, 1)
                        FillPortions: =0
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.End
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutMinHeight: =Parent.Height
                        RadiusBottomLeft: =6
                        RadiusBottomRight: =6
                        RadiusTopLeft: =6
                        RadiusTopRight: =6
                        Width: =200
                      Children:
                        - ButtonCanvas5:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              BasePaletteColor: =RGBA(33, 56, 194, 1)
                              BorderColor: =RGBA(33, 56, 194, 1)
                              BorderStyle: =RGBA(33, 56, 194, 1)
                              FontColor: =RGBA(40, 134, 222, 1)
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardoverview, ScreenTransition.Fade)
                              Text: ="Overview"
                              Width: =Parent.Width
                  - Container9_1:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        AlignInContainer: =AlignInContainer.SetByContainer
                        FillPortions: =0
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.End
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutMinHeight: =Parent.Height
                        Width: =200
                      Children:
                        - ButtonCanvas5_1:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              FontColor: =RGBA(0, 0, 0, 1)
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardAllApplicants, ScreenTransition.Fade)
                              Text: ="All Applicants"
                              Width: =Parent.Width
                  - Container9_2:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        AlignInContainer: =AlignInContainer.SetByContainer
                        FillPortions: =0
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.End
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutMinHeight: =Parent.Height
                        Width: =200
                      Children:
                        - ButtonCanvas5_2:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              FontColor: =RGBA(0, 0, 0, 1)
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardReports, ScreenTransition.Fade)
                              Text: ="Reports"
                              Width: =Parent.Width
            - Container10:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  FillPortions: =0
                  Height: =250
                  LayoutDirection: =LayoutDirection.Horizontal
                  Width: =Parent.Width
                Children:
                  - Container11:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        Width: =300
                      Children:
                        - Icon5:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="People"
                              Width: =Parent.Width
                        - Label4:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="3"
                              Width: =Parent.Width
                        - Label5:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Total Applications"
                              Width: =Parent.Width
                  - Container11_1:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        Width: =300
                      Children:
                        - Icon5_1:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="DocumentBulletList"
                              Width: =Parent.Width
                        - Label4_1:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="2"
                              Width: =Parent.Width
                        - Label5_1:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="New"
                              Width: =Parent.Width
                  - Container11_2:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        Width: =300
                      Children:
                        - Icon5_2:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="ArrowSync"
                              Width: =Parent.Width
                        - Label4_2:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="3"
                              Width: =Parent.Width
                        - Label5_2:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="In Progress"
                              Width: =Parent.Width
                  - Container11_3:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        Width: =300
                      Children:
                        - Icon5_3:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="CheckmarkCircle"
                              Width: =Parent.Width
                        - Label4_3:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="0"
                              Width: =Parent.Width
                        - Label5_3:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Approved"
                              Width: =Parent.Width
                  - Container11_4:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        Width: =300
                      Children:
                        - Icon5_4:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="DismissCircle"
                              Width: =Parent.Width
                        - Label4_4:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="0"
                              Width: =Parent.Width
                        - Label5_4:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Rejected"
                              Width: =Parent.Width
```

## Key Patterns
- **Header Layout**: Fixed height header (95px) with title/description on left, logout on right
- **Tab Navigation**: Horizontal button tabs with active state styling
- **Statistics Cards**: Equal-width containers (300px) with centered icon/number/label
- **Responsive Wrapping**: `LayoutWrap: =true` on navigation container
- **Clean Logout**: Resets form inputs and clears validation variables

## Navigation Targets
- Overview: `srcAdminDashboardoverview` (current)
- All Applicants: `srcAdminDashboardAllApplicants`
- Reports: `srcAdminDashboardReports`
- Logout: `scrLogin`

## Statistics Displayed
- Total Applications: 3
- New: 2
- In Progress: 3
- Approved: 0
- Rejected: 0

## Layout Structure
1. **Main Container**: Vertical layout with 16px gaps and padding
2. **Header Section**: Horizontal layout with title area and logout button
3. **Navigation Tabs**: Horizontal tabs with active state highlighting
4. **Statistics Grid**: Horizontal layout with 5 equal-width stat cards