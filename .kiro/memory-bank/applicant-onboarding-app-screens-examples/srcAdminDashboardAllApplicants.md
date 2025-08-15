# Admin Dashboard All Applicants (srcAdminDashboardAllApplicants)

## Overview
Admin screen showing list of all applicants with search, filter, and view functionality.

## Features
- Header with title, description, and logout button
- Navigation tabs (Overview, All Applicants, Reports)
- Search bar with text input and status filter dropdown
- Clear filters functionality
- Applicant list with name, phone, education, category, status, and view button
- Status color coding (New=blue, Ready for Review=orange, HR Review=orange)

## Screen Code
```yaml
Screens:
  srcAdminDashboardAllApplicants:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - Container7:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
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
            - Container5_2:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  BorderColor: =RGBA(214, 221, 224, 1)
                  DropShadow: =DropShadow.None
                  FillPortions: =0
                  Height: =95
                  LayoutDirection: =LayoutDirection.Horizontal
                  Width: =Parent.Width
                Children:
                  - Container29_1:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(0, 0, 0, 0)
                        DropShadow: =DropShadow.None
                        Height: =Parent.Height
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutMinHeight: =95
                      Children:
                        - Label1_2:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(33, 56, 194, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Size: =14
                              Text: ="Admin Dashboard"
                              Width: =Parent.Width
                        - Label2_2:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Color: =RGBA(40, 40, 40, 1)
                              Font: =Font.'Open Sans'
                              Text: ="Manage all users and application records • Logged in as System Administrator"
                              Width: =Parent.Width
                  - Container30_1:
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
                        - ButtonCanvas7_1:
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
            - Container8_2:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  BorderColor: =RGBA(0, 0, 0, 0)
                  DropShadow: =DropShadow.Semilight
                  FillPortions: =0
                  Height: =70
                  LayoutAlignItems: =LayoutAlignItems.End
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutWrap: =true
                  Width: =Parent.Width
                Children:
                  - Container9_6:
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
                        - ButtonCanvas5_3:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardoverview, ScreenTransition.Fade)
                              Text: ="Overview"
                              Width: =Parent.Width
                  - Container9_7:
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
                        - ButtonCanvas5_4:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              FontColor: =RGBA(40, 134, 222, 1)
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardAllApplicants, ScreenTransition.Fade)
                              Text: ="All Applicants"
                              Width: =Parent.Width
                  - Container9_8:
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
                        - ButtonCanvas5_5:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              Height: =Parent.Height
                              Icon: ="AppsListDetail"
                              OnSelect: =Navigate(srcAdminDashboardReports, ScreenTransition.Fade)
                              Text: ="Reports"
                              Width: =Parent.Width
            - Container13:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  FillPortions: =0
                  Height: =60
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutGap: =10
                Children:
                  - Container14:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(33, 56, 194, 1)
                        BorderThickness: =2
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutMinHeight: =60
                        LayoutMinWidth: =80
                        RadiusBottomLeft: =10
                        RadiusBottomRight: =10
                        RadiusTopLeft: =10
                        RadiusTopRight: =10
                      Children:
                        - Icon3:
                            Control: Icon@0.0.7
                            Properties:
                              Icon: ="Search"
                        - TextInputCanvas1:
                            Control: TextInput@0.0.54
                            Properties:
                              Fill: =RGBA(228, 228, 228, 1)
                              FillPortions: =1
                              Height: =Parent.Height
                              Placeholder: ="Search Applicants"
                  - Container14_1:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(33, 56, 194, 1)
                        BorderThickness: =2
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutMinHeight: =60
                        LayoutMinWidth: =80
                        RadiusBottomLeft: =10
                        RadiusBottomRight: =10
                        RadiusTopLeft: =10
                        RadiusTopRight: =10
                      Children:
                        - DropdownCanvas2:
                            Control: DropDown@0.0.45
                            Properties:
                              AccessibleLabel: ="All Statuses"
                              BorderColor: =RGBA(33, 56, 194, 1)
                              BorderStyle: =BorderStyle.Solid
                              BorderThickness: =0
                              DefaultSelectedItems: =LookUp(Statuses, 'Status Name' = "All Statuses")
                              Fill: =RGBA(228, 228, 228, 1)
                              FillPortions: =1
                              Height: =Parent.Height
                              Items: =Statuses
                            Children:
                              - Status Name1:
                                  Control: DropDownDataField@1.5.0
                                  Variant: textualColumn
                                  IsLocked: true
                                  Properties:
                                    FieldDisplayName: ="Status Name"
                                    FieldName: ="cr380_statusname"
                                    FieldType: ="s"
                                    Order: =1
                  - Container14_2:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        BorderColor: =RGBA(33, 56, 194, 1)
                        BorderThickness: =2
                        Height: =Parent.Height
                        LayoutAlignItems: =LayoutAlignItems.Center
                        LayoutDirection: =LayoutDirection.Horizontal
                        LayoutJustifyContent: =LayoutJustifyContent.Center
                        LayoutMinHeight: =60
                        LayoutMinWidth: =80
                        RadiusBottomLeft: =10
                        RadiusBottomRight: =10
                        RadiusTopLeft: =10
                        RadiusTopRight: =10
                      Children:
                        - ButtonCanvas3:
                            Control: Button@0.0.45
                            Properties:
                              Appearance: ='ButtonCanvas.Appearance'.Transparent
                              FillPortions: =1
                              FontColor: =RGBA(40, 134, 222, 1)
                              FontWeight: =FontWeight.Bold
                              Height: =Parent.Height
                              IconStyle: ='ButtonCanvas.IconStyle'.Outline
                              OnSelect: |
                                =Reset(DropdownCanvas2);
                                Reset(TextInputCanvas1)
                              Text: ="Clear Filters"
            - Container16:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  LayoutDirection: =LayoutDirection.Vertical
                Children:
                  - Container17:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        FillPortions: =0
                        Height: =60
                        LayoutDirection: =LayoutDirection.Vertical
                      Children:
                        - Label7:
                            Control: Label@2.5.1
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              Font: =Font.'Open Sans'
                              FontWeight: =FontWeight.Bold
                              Height: =Parent.Height
                              Text: ="All Applicants (3)"
                              Width: =Parent.Width
                  - Container12:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        LayoutDirection: =LayoutDirection.Vertical
                      Children:
                        - Container15:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =85
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container18:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          FontWeight: =FontWeight.Bold
                                          Text: ="John Smith"
                                          Width: =Parent.Width
                                    - Label9:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="+1-3232-1212"
                                          Width: =Parent.Width
                              - Container18_1:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_1:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Education"
                                          Width: =Parent.Width
                                    - Label9_1:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="Bachelor's Degree"
                                          Width: =Parent.Width
                              - Container18_2:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_2:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Category"
                                          Width: =Parent.Width
                                    - Label9_2:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="Bachelor's Degree"
                                          Width: =Parent.Width
                              - Container18_3:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label10:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(54, 176, 75, 1)
                                          Color: =RGBA(40, 134, 222, 1)
                                          DisabledColor: =RGBA(40, 134, 222, 1)
                                          DisplayMode: =DisplayMode.Disabled
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Size: =11
                                          Text: ="New"
                                          Width: =Parent.Width
                              - Container18_4:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - ButtonCanvas3_2:
                                        Control: Button@0.0.45
                                        Properties:
                                          Align: =Align.Center
                                          Appearance: ='ButtonCanvas.Appearance'.Transparent
                                          BorderStyle: =BorderStyle.Solid
                                          FillPortions: =1
                                          FontColor: =RGBA(0, 0, 0, 1)
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Icon: ="Eye"
                                          IconStyle: ='ButtonCanvas.IconStyle'.Outline
                                          OnSelect: =Navigate(srcAdminDashboardApplicantDetails, ScreenTransition.Fade)
                                          Text: ="View"
                                          Width: =Parent.Width
                        - Container15_1:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =85
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container18_5:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_3:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          FontWeight: =FontWeight.Bold
                                          Text: ="Sarah Johnson"
                                          Width: =Parent.Width
                                    - Label9_3:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="+1-555-0124"
                                          Width: =Parent.Width
                              - Container18_6:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_4:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Education"
                                          Width: =Parent.Width
                                    - Label9_4:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="Master's Degree"
                                          Width: =Parent.Width
                              - Container18_7:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_5:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Category"
                                          Width: =Parent.Width
                                    - Label9_5:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="Part-time"
                                          Width: =Parent.Width
                              - Container18_8:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label10_1:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(54, 176, 75, 1)
                                          Color: =RGBA(240, 98, 15, 1)
                                          DisabledBorderColor: =RGBA(1, 130, 64, 1)
                                          DisabledColor: =RGBA(45, 128, 40, 1)
                                          DisplayMode: =DisplayMode.Disabled
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Size: =11
                                          Text: ="Ready for Review"
                                          Width: =Parent.Width
                              - Container18_9:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - ButtonCanvas3_3:
                                        Control: Button@0.0.45
                                        Properties:
                                          Align: =Align.Center
                                          Appearance: ='ButtonCanvas.Appearance'.Transparent
                                          BorderStyle: =BorderStyle.Solid
                                          FillPortions: =1
                                          FontColor: =RGBA(0, 0, 0, 1)
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Icon: ="Eye"
                                          IconStyle: ='ButtonCanvas.IconStyle'.Outline
                                          OnSelect: =Navigate(srcAdminDashboardApplicantDetails, ScreenTransition.Fade)
                                          Text: ="View"
                                          Width: =Parent.Width
                        - Container15_2:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =85
                              LayoutDirection: =LayoutDirection.Horizontal
                              Width: =Parent.Width
                            Children:
                              - Container18_10:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_6:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          FontWeight: =FontWeight.Bold
                                          Text: ="Michael Brown"
                                          Width: =Parent.Width
                                    - Label9_6:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="+1-555-0126"
                                          Width: =Parent.Width
                              - Container18_11:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_7:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Education"
                                          Width: =Parent.Width
                                    - Label9_7:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="High School"
                                          Width: =Parent.Width
                              - Container18_12:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label8_8:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Lighter
                                          Size: =12
                                          Text: ="Category"
                                          Width: =Parent.Width
                                    - Label9_8:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          Font: =Font.'Open Sans'
                                          Size: =12
                                          Text: ="Contract"
                                          Width: =Parent.Width
                              - Container18_13:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - Label10_2:
                                        Control: Label@2.5.1
                                        Properties:
                                          Align: =Align.Center
                                          BorderColor: =RGBA(54, 176, 75, 1)
                                          Color: =RGBA(240, 98, 15, 1)
                                          DisabledBorderColor: =RGBA(1, 130, 64, 1)
                                          DisabledColor: =RGBA(1, 130, 64, 1)
                                          DisplayMode: =DisplayMode.Disabled
                                          Font: =Font.'Lato Light'
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Size: =11
                                          Text: ="HR Review"
                                          Width: =Parent.Width
                              - Container18_14:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    BorderColor: =RGBA(0, 0, 0, 0)
                                    DropShadow: =DropShadow.None
                                    LayoutAlignItems: =LayoutAlignItems.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutMinHeight: =85
                                  Children:
                                    - ButtonCanvas3_4:
                                        Control: Button@0.0.45
                                        Properties:
                                          Align: =Align.Center
                                          Appearance: ='ButtonCanvas.Appearance'.Transparent
                                          BorderStyle: =BorderStyle.Solid
                                          FillPortions: =1
                                          FontColor: =RGBA(0, 0, 0, 1)
                                          FontWeight: =FontWeight.Bold
                                          Height: =Parent.Height
                                          Icon: ="Eye"
                                          IconStyle: ='ButtonCanvas.IconStyle'.Outline
                                          OnSelect: =Navigate(srcAdminDashboardApplicantDetails, ScreenTransition.Fade)
                                          Text: ="View"
                                          Width: =Parent.Width
```

## Key Patterns
- **Search & Filter Bar**: Horizontal layout with search input, status dropdown, and clear filters button
- **Applicant List**: Vertical list with 85px height rows containing 5 columns (Name/Phone, Education, Category, Status, Actions)
- **Status Color Coding**: Blue for "New", Orange for "Ready for Review" and "HR Review"
- **Consistent Navigation**: Same header and tab structure as overview screen
- **View Button**: Eye icon button that navigates to applicant details

## Navigation Targets
- Overview: `srcAdminDashboardoverview`
- All Applicants: `srcAdminDashboardAllApplicants` (current)
- Reports: `srcAdminDashboardReports`
- View Details: `srcAdminDashboardApplicantDetails`
- Logout: `scrLogin`

## Data Sources
- `Statuses`: Collection for status dropdown filter
- Field mapping: `cr380_statusname` for status field

## Applicants Displayed
1. **John Smith** - +1-3232-1212, Bachelor's Degree, Status: New (Blue)
2. **Sarah Johnson** - +1-555-0124, Master's Degree, Part-time, Status: Ready for Review (Orange)
3. **Michael Brown** - +1-555-0126, High School, Contract, Status: HR Review (Orange)

## Filter Controls
- **Search**: Text input for searching applicants
- **Status Filter**: Dropdown with "All Statuses" default
- **Clear Filters**: Resets both search and status filter