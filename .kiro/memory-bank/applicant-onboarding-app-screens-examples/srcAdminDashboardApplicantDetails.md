# Admin Dashboard Applicant Details (srcAdminDashboardApplicantDetails)

## Overview
Detailed view screen for individual applicant information with form fields and navigation controls.

## Features
- Header with applicant name and back button
- Basic Information section with disabled form fields
- Two-column layout for form fields (Name/Phone, Email/Education, Category/Created)
- Cancel button to return to applicant list
- Read-only form display with placeholder values

## Screen Code
```yaml
Screens:
  srcAdminDashboardApplicantDetails:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - Container1_3:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            BorderColor: =RGBA(0, 0, 0, 0)
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
            - Container19:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  BorderColor: =RGBA(0, 0, 0, 0)
                  FillPortions: =0
                  Height: =95
                  LayoutDirection: =LayoutDirection.Horizontal
                Children:
                  - Container26:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        Height: =Parent.Height
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =80
                      Children:
                        - Label11:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(33, 56, 194, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Size: =14
                              Text: ="John Smith"
                              Width: =Parent.Width
                        - Label11_1:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(40, 40, 40, 1)
                              Font: =Font.'Lato Light'
                              Text: ="Applicant Profile"
                              Width: =Parent.Width
                  - Container27:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutJustifyContent: =LayoutJustifyContent.End
                        LayoutMinHeight: =80
                      Children:
                        - ButtonCanvas6:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              BorderColor: =RGBA(33, 56, 194, 1)
                              BorderStyle: =BorderStyle.Solid
                              BorderThickness: =2
                              Icon: ="ArrowLeft"
                              OnSelect: =Navigate(srcAdminDashboardAllApplicants, ScreenTransition.Fade)
                              Text: ="Back"
            - Container20:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  LayoutDirection: =LayoutDirection.Vertical
                  LayoutGap: =10
                Children:
                  - Container21:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        FillPortions: =0
                        Height: =50
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =10
                      Children:
                        - Label13:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Height: =Parent.Height
                              Size: =14.5
                              Text: ="Basic Information"
                              Width: =Parent.Width
                  - Container22:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Height: =Parent.Height
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =10
                        Width: =Parent.Width
                      Children:
                        - Container24:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =90
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container25:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Name"
                                          Width: =Parent.Width
                                    - TextInputCanvas2:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="John Smith"
                                          Width: =Parent.Width
                              - Container25_1:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14_1:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Phone"
                                          Width: =Parent.Width
                                    - TextInputCanvas2_1:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="+1-555-0123"
                                          Width: =Parent.Width
                        - Container24_1:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =90
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container25_2:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14_2:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Email"
                                          Width: =Parent.Width
                                    - TextInputCanvas2_2:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="john.smith@email.com"
                                          Width: =Parent.Width
                              - Container25_3:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14_3:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Education"
                                          Width: =Parent.Width
                                    - TextInputCanvas2_3:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="Bachelor's Degree"
                                          Width: =Parent.Width
                        - Container24_2:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =90
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container25_4:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14_4:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Category"
                                          Width: =Parent.Width
                                    - TextInputCanvas2_4:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="Full-time"
                                          Width: =Parent.Width
                              - Container25_5:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    Height: =80
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =50
                                    PaddingLeft: =5
                                  Children:
                                    - Label14_5:
                                        Control: Label@2.5.1
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          Font: =Font.'Open Sans'
                                          PaddingBottom: =0
                                          PaddingLeft: =0
                                          PaddingRight: =0
                                          PaddingTop: =0
                                          Text: ="Created"
                                          Width: =Parent.Width
                                    - TextInputCanvas2_5:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          DisplayMode: =DisplayMode.Disabled
                                          FillPortions: =1
                                          Placeholder: ="1/15/2024"
                                          Width: =Parent.Width
                        - ButtonCanvas4:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              BorderColor: =RGBA(33, 56, 194, 1)
                              BorderStyle: =BorderStyle.Solid
                              BorderThickness: =2
                              OnSelect: =Navigate(srcAdminDashboardAllApplicants, ScreenTransition.Fade)
                              Text: ="Cancel"
```

## Key Patterns
- **Header Layout**: Applicant name on left, back button on right
- **Two-Column Form**: Pairs of fields in horizontal containers (Name/Phone, Email/Education, Category/Created)
- **Disabled Inputs**: All TextInput controls use `DisplayMode.Disabled` for read-only display
- **Placeholder Values**: Data shown through placeholder text instead of actual values
- **Consistent Spacing**: 10px gaps between form sections, 5px left padding on field containers
- **Navigation Buttons**: Back button in header, Cancel button at bottom

## Navigation Targets
- Back: `srcAdminDashboardAllApplicants`
- Cancel: `srcAdminDashboardAllApplicants`

## Applicant Data Displayed
- **Name**: John Smith
- **Phone**: +1-555-0123
- **Email**: john.smith@email.com
- **Education**: Bachelor's Degree
- **Category**: Full-time
- **Created**: 1/15/2024

## Form Structure
1. **Header Section**: Name/title with back button (95px height)
2. **Section Title**: "Basic Information" label (50px height)
3. **Form Rows**: Three horizontal rows with two fields each (90px height each)
4. **Action Button**: Cancel button at bottom

## Field Layout Pattern
Each form row contains two equal-width containers:
- Left container: Label + TextInput
- Right container: Label + TextInput
- Both containers have 5px left padding and 80px height
- Labels use FillPortions=1 for flexible sizing