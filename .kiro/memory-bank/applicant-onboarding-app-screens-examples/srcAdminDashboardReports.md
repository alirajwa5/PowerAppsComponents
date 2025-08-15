# Admin Dashboard Reports (srcAdminDashboardReports)

## Overview
Admin reports screen showing key performance metrics and conversion rates for the applicant onboarding process.

## Features
- Header with title, description, and logout button
- Navigation tabs (Overview, All Applicants, Reports)
- Color-coded metric cards showing conversion rates and statistics
- Visual KPI dashboard with percentage-based metrics

## Screen Code
```yaml
Screens:
  srcAdminDashboardReports:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - Container1_2:
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
            - Container5_1:
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
                  - Container29_2:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        Height: =Parent.Height
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =95
                      Children:
                        - Label1_1:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(33, 56, 194, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Size: =14
                              Text: ="Admin Dashboard"
                              Width: =Parent.Width
                        - Label2_1:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(40, 40, 40, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Manage all users and application records • Logged in as System Administrator"
                              Width: =Parent.Width
                  - Container30_2:
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
                        - ButtonCanvas7_2:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              BasePaletteColor: =RGBA(33, 56, 194, 1)
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
            - Container8_1:
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
                  - Container9_3:
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
                        - ButtonCanvas5_6:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardoverview, ScreenTransition.Fade)
                              Text: ="Overview"
                              Width: =Parent.Width
                  - Container9_4:
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
                        - ButtonCanvas5_7:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardAllApplicants, ScreenTransition.Fade)
                              Text: ="All Applicants"
                              Width: =Parent.Width
                  - Container9_5:
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
                        - ButtonCanvas5_8:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              FontColor: =RGBA(40, 134, 222, 1)
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardReports, ScreenTransition.Fade)
                              Text: ="Reports"
                              Width: =Parent.Width
            - Container10_1:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  FillPortions: =0
                  Height: =80
                  LayoutDirection: =LayoutDirection.Horizontal
                  Width: =Parent.Width
                Children:
                  - Container6:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(174, 208, 221, 1)
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =80
                      Children:
                        - Label6:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(40, 134, 222, 1)
                              Font: =Font.'Open Sans'
                              Size: =10
                              Text: ="Conversion Rate"
                        - Label6_1:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Text: ="0.0%"
                  - Container6_1:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 184, 174, 1)
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =80
                      Children:
                        - Label6_2:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(215, 58, 60, 1)
                              Font: =Font.'Open Sans'
                              Size: =10
                              Text: ="Rejection Rate"
                        - Label6_3:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Text: ="0.0%"
                  - Container6_2:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(253, 207, 180, 1)
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =80
                      Children:
                        - Label6_4:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(240, 98, 15, 1)
                              Font: =Font.'Open Sans'
                              Size: =10
                              Text: ="In Progress"
                        - Label6_5:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Text: ="66.7%"
                  - Container6_3:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(166, 215, 153, 1)
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =80
                      Children:
                        - Label6_6:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(52, 152, 47, 1)
                              Font: =Font.'Open Sans'
                              Size: =10
                              Text: ="Success Rate"
                        - Label6_7:
                            Control: Label@2.5.1
                            Properties:
                              Align: =Align.Center
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Text: ="0.0%"
```

## Key Patterns
- **Color-Coded Metrics**: Each metric has distinct background and text colors
- **Equal Width Cards**: 4 metric cards with equal spacing in horizontal layout
- **Centered Content**: All text centered within each metric card
- **Consistent Navigation**: Same header and tab structure as other admin screens
- **Visual Hierarchy**: Small label text (size 10) with bold percentage values

## Navigation Targets
- Overview: `srcAdminDashboardoverview`
- All Applicants: `srcAdminDashboardAllApplicants`
- Reports: `srcAdminDashboardReports` (current)
- Logout: `scrLogin`

## Metrics Displayed
1. **Conversion Rate**: 0.0% (Blue theme - RGBA(174, 208, 221, 1))
2. **Rejection Rate**: 0.0% (Red theme - RGBA(255, 184, 174, 1))
3. **In Progress**: 66.7% (Orange theme - RGBA(253, 207, 180, 1))
4. **Success Rate**: 0.0% (Green theme - RGBA(166, 215, 153, 1))

## Color Scheme
- **Blue Card**: Light blue background with blue text (RGBA(40, 134, 222, 1))
- **Red Card**: Light red background with red text (RGBA(215, 58, 60, 1))
- **Orange Card**: Light orange background with orange text (RGBA(240, 98, 15, 1))
- **Green Card**: Light green background with green text (RGBA(52, 152, 47, 1))

## Layout Structure
1. **Main Container**: Vertical layout with 16px gaps and padding
2. **Header Section**: Horizontal layout with title area and logout button
3. **Navigation Tabs**: Horizontal tabs with "Reports" highlighted
4. **Metrics Row**: Horizontal layout with 4 equal-width metric cards (80px height)