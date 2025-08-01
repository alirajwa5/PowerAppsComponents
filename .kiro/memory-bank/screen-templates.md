# Power Apps Screen Templates

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

### Key Features

- **Horizontal Layout**: ScreenContainer uses `LayoutDirection.Horizontal`
- **Equal Split**: Both containers get equal space (no FillPortions specified)
- **Responsive**: `LayoutWrap: true` allows stacking on smaller screens
- **Consistent Styling**: Both containers have same fill color and radius
- **Proper Spacing**: 16px gap between containers and screen padding

### Use Cases

- **Master-Detail**: List on left, details on right
- **Comparison Views**: Compare two items side by side
- **Form Sections**: Split complex forms into logical sections
- **Dashboard Panels**: Different data views in each panel
- **Settings Pages**: Categories on left, options on right

### Responsive Behavior

- **Desktop**: Two columns side by side
- **Mobile**: Stacks vertically due to `LayoutWrap: true`
- **Tablet**: Maintains side-by-side layout

### Customization Options

- **Unequal Split**: Add `FillPortions` (e.g., left=1, right=2 for 1:2 ratio)
- **Different Colors**: Change Fill colors for visual distinction
- **Shadows**: Add `DropShadow` properties for elevation
- **Spacing**: Adjust `LayoutGap` for tighter/looser spacing

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

### Key Features

- **Three-Section Layout**: Header (fixed) + Sidebar + Main Content
- **Proportional Sizing**: Sidebar (30%) vs Main (70%) using FillPortions
- **Vertical Screen Flow**: Header stacked above horizontal content area
- **Responsive Wrapping**: `LayoutWrap: true` for mobile adaptation
- **Minimal Padding**: 2px padding in BottomContainer for tight spacing

### Use Cases

- **Admin Dashboards**: Navigation sidebar with main dashboard
- **Settings Pages**: Category sidebar with settings panels
- **File Browsers**: Folder tree sidebar with file list
- **Documentation**: Table of contents sidebar with content
- **E-commerce**: Category filters sidebar with product grid

### Layout Hierarchy

1. **ScreenContainer**: Vertical layout (Header + Content)
2. **HeaderContainer**: Fixed height header (75px)
3. **BottomContainer**: Horizontal layout wrapper
4. **SidebarContainer**: Navigation/menu area (30% width)
5. **MainContainer**: Primary content area (70% width)

### Responsive Behavior

- **Desktop**: Sidebar + Main side by side
- **Mobile**: Stacks vertically (sidebar above main)
- **Header**: Always stays at top across all screen sizes

### Customization Options

- **Sidebar Width**: Adjust FillPortions ratio (e.g., 2:8 for narrower sidebar)
- **Collapsible Sidebar**: Add visibility conditions for mobile
- **Different Backgrounds**: Distinguish sidebar with different Fill color
- **Header Height**: Modify Height property for taller/shorter headers

## Approval Request Form Template

### Overview

A comprehensive form layout for approval workflows with a main form area (70%) and reviewer sidebar (30%). Features a complete data entry form with various field types and an approval workflow tracker.

### Structure

```yaml
Screens:
  ApprovalRequestScreen:
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
                Children:
                  - Header:
                      Control: Header@0.0.44
                      Properties:
                        Title: ="Header"
            - MainContainer:
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
                  - FormContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 255, 255, 1)
                        FillPortions: =7
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =16
                        PaddingBottom: =15
                        PaddingLeft: =15
                        PaddingRight: =15
                        PaddingTop: =15
                        RadiusBottomLeft: =8
                        RadiusBottomRight: =8
                        RadiusTopLeft: =8
                        RadiusTopRight: =8
                      Children:
                        - FormTitle:
                            Control: Text@0.0.51
                            Properties:
                              Align: ='TextCanvas.Align'.End
                              Size: =20
                              Text: ="Request approval"
                              Weight: ='TextCanvas.Weight'.Semibold
                              Width: =180
                        - ApprovalForm:
                            Control: Form@2.4.4
                            Layout: Vertical
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              DataSource: =Applicant
                              DefaultMode: =FormMode.New
                              NumberOfColumns: =1
                            Children:
                              # Multiple TypedDataCard controls for form fields
                        - SubmitButton:
                            Control: Button@0.0.45
                            Properties:
                              AccessibleLabel: ="Submit approval request button"
                              AlignInContainer: =AlignInContainer.End
                              OnSelect: |
                                =SubmitForm(ApprovalForm);
                                ResetForm(ApprovalForm);
                              Text: ="Submit request"
                              Width: =140
                  - SidebarContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 255, 255, 1)
                        FillPortions: =2
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =16
                        PaddingTop: =15
                        RadiusBottomLeft: =8
                        RadiusBottomRight: =8
                        RadiusTopLeft: =8
                        RadiusTopRight: =8
                        Visible: =If(Screen.Size = ScreenSize.Small, false, true)
                      Children:
                        - ReviewersTitle:
                            Control: Text@0.0.51
                            Properties:
                              Align: ='TextCanvas.Align'.End
                              Size: =20
                              Text: ="Reviewers"
                              Weight: ='TextCanvas.Weight'.Semibold
                              Width: =115
                        - ReviewersGallery:
                            Control: Gallery@2.15.0
                            Variant: Vertical
                            Properties:
                              Items: =[
                                {Step: 1, Name: "Name", Title: "Title", Status: "Approved", Current: true},
                                {Step: 2, Name: "Name", Title: "Title", Status: "Pending"},
                                {Step: 3, Name: "Name", Title: "Title", Status: "Not Started"}
                              ]
                              TemplateSize: =If(Screen.Size = ScreenSize.Small, 80, 140)
                            Children:
                              - StatusBadge:
                                  Control: Badge@0.0.24
                                  Properties:
                                    BasePaletteColor: =Switch(
                                      ThisItem.Status,
                                      "Pending", Color.DarkGoldenRod,
                                      "Approved", Color.DarkGreen,
                                      "Rejected", Color.Red
                                    )
                                    Content: =Left(ThisItem.Status, 1)
                              - ReviewerName:
                                  Control: Text@0.0.51
                                  Properties:
                                    Text: =ThisItem.Name
                                    Weight: =If(ThisItem.Current, "Bold", "Regular")
```

### Key Features

- **Form-Sidebar Layout**: 7:2 ratio (70% form, 30% sidebar)
- **Complete Form**: Multiple field types (text, date, dropdown, combobox)
- **Approval Workflow**: Visual reviewer progress with badges
- **Responsive Sidebar**: Hides on small screens
- **Modern Controls**: Uses Text@0.0.51, Button@0.0.45, Badge@0.0.24
- **Form Validation**: Built-in error handling and required field indicators

### Form Field Types Demonstrated

- **TextInput**: First Name, Last Name, City, Country, WhatsApp, Occupation
- **DatePicker**: Date of Birth with time selectors
- **ComboBox**: Education Level, Applicant Category, Status (choice fields)
- **Form Validation**: Error messages, required field indicators

### Approval Workflow Features

- **Status Badges**: Color-coded approval states
- **Progress Tracking**: Visual workflow with connecting lines
- **Reviewer Information**: Names, titles, current step highlighting
- **Responsive Design**: Adapts to screen size

### Use Cases

- **Approval Workflows**: Document, expense, leave approvals
- **Application Forms**: Job applications, registrations
- **Review Processes**: Multi-step approval chains
- **Data Entry**: Complex forms with validation
- **Workflow Tracking**: Visual progress indicators

### Customization Options

- **Field Types**: Add/remove form fields as needed
- **Approval Steps**: Modify reviewer workflow
- **Validation Rules**: Customize required fields and validation
- **Styling**: Adjust colors, spacing, and layout proportions

## Header and Footer Template

### Overview

A classic header and footer layout where the "footer" is actually the main content area containing sidebar and main sections. This creates a header-body structure commonly used in Power Apps.

### Structure

```yaml
Screens:
  HeaderFooterScreen:
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

### Key Features

- **Fixed Header**: HeaderContainer with FillPortions=0 and fixed Height=75
- **Flexible Body**: BottomContainer takes remaining space
- **Nested Layout**: BottomContainer contains sidebar and main content
- **Minimal Padding**: 2px padding in BottomContainer for tight layout
- **Consistent Styling**: All containers have 8px radius

### Layout Hierarchy

1. **ScreenContainer**: Vertical layout (Header + Body)
2. **HeaderContainer**: Fixed height header area
3. **BottomContainer**: Flexible content wrapper
4. **SidebarContainer**: Left navigation (30% width)
5. **MainContainer**: Primary content (70% width)

### Power Apps Pattern

This is the standard Power Apps "Header and Footer" template where:

- **Header**: Navigation, branding, user info
- **Footer** (BottomContainer): Main application content area
- The "footer" contains the actual app functionality

### Use Cases

- **Application Shells**: Consistent header across all screens
- **Navigation Layouts**: Header with logo/menu, content below
- **Dashboard Layouts**: Header with controls, data below
- **Multi-Section Apps**: Header for global actions, content for features

### Responsive Behavior

- **Header**: Always fixed at top
- **Content**: Sidebar and main can wrap on mobile
- **Proportions**: Maintains 3:7 ratio on larger screens

### Customization Options

- **Header Height**: Adjust Height property for different header sizes
- **Content Ratio**: Change FillPortions for different sidebar/main proportions
- **Padding**: Modify LayoutGap and padding for spacing preferences
- **Backgrounds**: Different Fill colors for visual hierarchy

## Header and Gallery Template

### Overview

A responsive gallery layout with header and card-based content display. Features responsive grid that adapts from 3 columns (ExtraLarge) to 2 columns (Large) to 1 column (Small screens).

### Structure

```yaml
Screens:
  HeaderGalleryScreen:
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
                Children:
                  - Header:
                      Control: Header@0.0.44
                      Properties:
                        Title: ="Header"
            - MainContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  Fill: =Parent.Fill
                  LayoutAlignItems: =LayoutAlignItems.Stretch
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutWrap: =true
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
                  Width: =1000
                Children:
                  - ItemsGallery:
                      Control: Gallery@2.15.0
                      Variant: Vertical
                      Properties:
                        AccessibleLabel: ="Items gallery"
                        BorderColor: =RGBA(0, 18, 107, 1)
                        TemplatePadding: =0
                        TemplateSize: =320
                        Transition: =Transition.Pop
                        WrapCount: =If(
                          Screen.Size = ScreenSize.ExtraLarge, 3,
                          Screen.Size = ScreenSize.Large, 2,
                          1
                        )
                      Children:
                        - GalleryContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              Fill: =RGBA(255, 255, 255, 1)
                              Height: =308
                              LayoutAlignItems: =LayoutAlignItems.Center
                              LayoutDirection: =LayoutDirection.Vertical
                              LayoutJustifyContent: =LayoutJustifyContent.Center
                              LayoutOverflowY: =LayoutOverflow.Scroll
                              Width: =If(
                                Screen.Size = ScreenSize.ExtraLarge, (Parent.Width / 3) - 15,
                                Screen.Size = ScreenSize.Large, (Parent.Width / 2) - 15,
                                Parent.Width
                              )
                              X: =5
                              Y: =5
                            Children:
                              - ImageContainer:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    FillPortions: =1.5
                                    LayoutAlignItems: =LayoutAlignItems.Stretch
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutGap: =5
                                    LayoutJustifyContent: =LayoutJustifyContent.End
                                    Width: =Parent.Width
                                  Children:
                                    - ItemImage:
                                        Control: Image@2.2.3
                                        Properties:
                                          BorderColor: =RGBA(0, 18, 107, 1)
                                          FillPortions: =1
                                          ImagePosition: =ImagePosition.Fill
                                          Width: =Parent.Width
                              - TitleContainer:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    AlignInContainer: =AlignInContainer.Center
                                    LayoutDirection: =LayoutDirection.Vertical
                                    LayoutGap: =8
                                    PaddingBottom: =20
                                    PaddingLeft: =20
                                    PaddingRight: =20
                                    PaddingTop: =20
                                    Width: =Parent.Width
                                  Children:
                                    - TitleText:
                                        Control: Text@0.0.51
                                        Properties:
                                          Height: =30
                                          Size: =16
                                          Text: ="Featured item"
                                          VerticalAlign: =VerticalAlign.Top
                                          Weight: ='TextCanvas.Weight'.Bold
                                          Width: =Parent.Width - TitleContainer.PaddingLeft
                                    - DescriptionText:
                                        Control: Text@0.0.51
                                        Properties:
                                          Height: =45
                                          Size: =16
                                          Text: ="Short description or engaging message"
                                          VerticalAlign: =VerticalAlign.Top
                                          Width: =Parent.Width - TitleContainer.PaddingLeft
                              - ButtonContainer:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    FillPortions: =0
                                    Height: =50
                                    LayoutDirection: =LayoutDirection.Vertical
                                    PaddingBottom: =12
                                    PaddingLeft: =20
                                    PaddingRight: =20
                                    PaddingTop: =8
                                    Width: =Parent.Width
                                  Children:
                                    - ActionButton:
                                        Control: Button@0.0.45
                                        Properties:
                                          AccessibleLabel: ="Featured item button"
                                          Appearance: ='ButtonCanvas.Appearance'.Secondary
                                          Width: =110
```

### Key Features

- **Responsive Grid**: 3/2/1 columns based on screen size
- **Card Layout**: Image + Title + Description + Button structure
- **Modern Gallery**: Uses WrapCount for responsive columns
- **Flexible Sizing**: Dynamic width calculation per screen size
- **Scroll Support**: LayoutOverflowY for content overflow
- **Clean Cards**: White background with proper spacing

### Responsive Behavior

- **ExtraLarge**: 3 columns, (Parent.Width / 3) - 15 per card
- **Large**: 2 columns, (Parent.Width / 2) - 15 per card
- **Small**: 1 column, Parent.Width per card
- **Gallery**: Uses WrapCount property for automatic wrapping

### Card Structure

1. **GalleryContainer**: Main card wrapper (308px height)
2. **ImageContainer**: Image section with FillPortions=1.5
3. **TitleContainer**: Text content with 20px padding
4. **ButtonContainer**: Action button area

### Use Cases

- **Product Catalogs**: E-commerce item displays
- **Content Galleries**: Blog posts, articles, media
- **Dashboard Cards**: Feature highlights, metrics
- **Portfolio Displays**: Projects, case studies
- **News Feeds**: Article previews with images

### Modern Controls Used

- **Gallery@2.15.0**: With Vertical variant and WrapCount
- **Image@2.2.3**: With ImagePosition.Fill
- **Text@0.0.51**: For titles and descriptions
- **Button@0.0.45**: With Secondary appearance

### Customization Options

- **Column Count**: Modify WrapCount logic for different breakpoints
- **Card Height**: Adjust TemplateSize for taller/shorter cards
- **Image Ratio**: Change FillPortions on ImageContainer
- **Spacing**: Modify padding and LayoutGap values
- **Transitions**: Change Transition property for different animations

## Header and Form View Template

### Overview

A dedicated form layout with header and scrollable form container. Features a single-column form with comprehensive field types and action buttons. Perfect for data entry and editing scenarios.

### Structure

```yaml
Screens:
  HeaderFormScreen:
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
                  AlignInContainer: =AlignInContainer.SetByContainer
                  FillPortions: =0
                  Height: =75
                  LayoutDirection: =LayoutDirection.Horizontal
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
                Children:
                  - Header:
                      Control: Header@0.0.44
                      Properties:
                        Title: ="Header"
            - MainContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  LayoutAlignItems: =LayoutAlignItems.Stretch
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutGap: =16
                  LayoutWrap: =true
                  PaddingBottom: =2
                  PaddingLeft: =2
                  PaddingRight: =2
                  PaddingTop: =2
                Children:
                  - FormContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        AlignInContainer: =AlignInContainer.SetByContainer
                        FillPortions: =7
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =16
                        LayoutOverflowY: =LayoutOverflow.Scroll
                        PaddingBottom: =15
                        PaddingLeft: =15
                        PaddingRight: =15
                        PaddingTop: =15
                        RadiusBottomLeft: =8
                        RadiusBottomRight: =8
                        RadiusTopLeft: =8
                        RadiusTopRight: =8
                      Children:
                        - DataForm:
                            Control: Form@2.4.4
                            Layout: Vertical
                            Properties:
                              BorderColor: =RGBA(0, 18, 107, 1)
                              DataSource: =Applicant
                              DefaultMode: =FormMode.New
                              NumberOfColumns: =1
                            Children:
                              # Multiple TypedDataCard controls for form fields
                              - FirstName_DataCard:
                                  Control: TypedDataCard@1.0.7
                                  Variant: TextualEdit
                                  Properties:
                                    BorderColor: =RGBA(0, 18, 107, 1)
                                    DataField: ="cr380_firstname"
                                    Default: =ThisItem.FirstName
                                    DisplayName: =DataSourceInfo([@Applicant], DataSourceInfo.DisplayName, 'cr380_firstname')
                                    Required: =false
                                    Update: =DataCardValue.Value
                                    Width: =1300
                                  Children:
                                    - DataCardKey:
                                        Control: Text@0.0.51
                                        Properties:
                                          Height: =22
                                          Text: =Parent.DisplayName
                                          Weight: ='TextCanvas.Weight'.Semibold
                                          Width: =Parent.Width - 48
                                          X: =24
                                          Y: =10
                                    - DataCardValue:
                                        Control: TextInput@0.0.54
                                        Properties:
                                          AccessibleLabel: =Parent.DisplayName
                                          DisplayMode: =Parent.DisplayMode
                                          Mode: ="'TextInputCanvas.Mode'.TextInputModeSingleLine"
                                          Required: =Parent.Required
                                          ValidationState: =If(IsBlank(Parent.Error), "None", "Error")
                                          Value: =Parent.Default
                                          Width: =Parent.Width - 48
                                          X: =24
                                          Y: =DataCardKey.Y + DataCardKey.Height + 4
                        - ButtonContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =50
                              LayoutDirection: =LayoutDirection.Horizontal
                              LayoutGap: =10
                              LayoutJustifyContent: =LayoutJustifyContent.End
                              PaddingBottom: =10
                              PaddingRight: =24
                              PaddingTop: =10
                            Children:
                              - CancelButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    AccessibleLabel: ="Cancel form button"
                                    AlignInContainer: =AlignInContainer.Center
                                    Appearance: ='ButtonCanvas.Appearance'.Secondary
                                    OnSelect: =ResetForm(DataForm)
                                    Text: ="Cancel"
                                    Width: =120
                              - SubmitButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    AccessibleLabel: ="Submit form button"
                                    AlignInContainer: =AlignInContainer.Center
                                    OnSelect: |
                                      =SubmitForm(DataForm);
                                      ResetForm(DataForm);
                                    Text: ="Submit"
                                    Width: =120
```

### Key Features

- **Scrollable Form**: LayoutOverflowY=Scroll for long forms
- **Single Column Layout**: NumberOfColumns=1 for clean vertical flow
- **Full Form Width**: Width=1300 for wide form fields
- **Comprehensive Fields**: Text, Date, ComboBox field types
- **Action Buttons**: Cancel (Secondary) and Submit (Primary) buttons
- **Form Validation**: Built-in error handling and required field indicators

### Form Field Structure

Each TypedDataCard contains:

1. **DataCardKey**: Field label with semibold weight
2. **DataCardValue**: Input control (TextInput, DatePicker, ComboBox)
3. **ErrorMessage**: Validation error display
4. **StarVisible**: Required field indicator (\*)

### Field Types Demonstrated

- **TextInput@0.0.54**: Single-line text fields
- **DatePicker@0.0.46**: Date selection with time dropdowns
- **ComboBox@0.0.51**: Choice/lookup fields
- **DropDown@0.0.45**: Hour/minute time selectors

### Button Layout

- **Horizontal Layout**: Side-by-side Cancel and Submit buttons
- **Right Alignment**: LayoutJustifyContent.End
- **Consistent Sizing**: Both buttons 120px width
- **Proper Spacing**: 10px gap between buttons

### Use Cases

- **Data Entry Forms**: New record creation
- **Edit Forms**: Existing record modification
- **Registration Forms**: User signup/onboarding
- **Settings Pages**: Configuration forms
- **Survey Forms**: Data collection

### Responsive Features

- **Scrollable Content**: Handles long forms gracefully
- **Fixed Header**: Always visible navigation
- **Flexible Form**: Adapts to content height
- **Wide Fields**: 1300px width for desktop optimization

### Customization Options

- **Form Columns**: Change NumberOfColumns for multi-column layout
- **Field Width**: Adjust Width property for narrower/wider fields
- **Button Actions**: Customize OnSelect for different workflows
- **Validation**: Add custom validation rules to fields
- **Styling**: Modify colors, spacing, and typography

## Header and Table Template

### Overview

A clean data display layout with header and modern Table control. Perfect for displaying tabular data with responsive behavior and professional styling.

### Structure

```yaml
Screens:
  HeaderTableScreen:
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
                  FillPortions: =0
                  Height: =75
                  LayoutDirection: =LayoutDirection.Horizontal
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
                Children:
                  - Header:
                      Control: Header@0.0.44
                      Properties:
                        Title: ="Header"
            - MainContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  LayoutAlignItems: =LayoutAlignItems.Stretch
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutWrap: =true
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
                  Width: =1000
                Children:
                  - DataTable:
                      Control: Table@1.0.278
                      Properties:
                        FillPortions: =1
                        ReflowBehavior: ='PowerAppsOneGrid.ReflowBehavior'.Reflow
                        Items: =DataSource
                      Children:
                        # TableDataField controls would be added here
                        - FieldName:
                            Control: TableDataField@1.5.0
                            Variant: textualColumn
                            IsLocked: true
                            Properties:
                              FieldDisplayName: ="Field Name"
                              FieldName: ="field_name"
                              FieldType: ="s"
                              Order: =1
```

### Key Features

- **Modern Table Control**: Table@1.0.278 with responsive behavior
- **Reflow Behavior**: Automatically adapts to screen size
- **Fixed Header**: Header stays at top with FillPortions=0
- **Flexible Table**: FillPortions=1 takes remaining space
- **Clean Layout**: Consistent 8px radius and proper spacing

### Table Properties

- **FillPortions=1**: Table takes all available space
- **ReflowBehavior.Reflow**: Responsive column behavior
- **Width=1000**: Fixed width for desktop optimization
- **LayoutWrap=true**: Allows wrapping on smaller screens

### Layout Hierarchy

1. **ScreenContainer**: Vertical layout (Header + Table)
2. **HeaderContainer**: Fixed height header (75px)
3. **MainContainer**: Flexible table wrapper
4. **DataTable**: Modern table control with data fields

### Table Field Structure

Each TableDataField would contain:

- **FieldDisplayName**: Column header text
- **FieldName**: Data source field mapping
- **FieldType**: Data type ("s"=string, "d"=date, "l"=lookup, "n"=number)
- **Order**: Column display order
- **Variant**: textualColumn, dateColumn, etc.

### Use Cases

- **Data Dashboards**: Display large datasets
- **Admin Panels**: User management, content management
- **Reports**: Financial data, analytics
- **Inventory Systems**: Product listings, stock levels
- **CRM Systems**: Contact lists, opportunity tracking

### Responsive Behavior

- **Desktop**: Full table with all columns visible
- **Tablet**: Columns may reflow based on ReflowBehavior
- **Mobile**: Table adapts with horizontal scrolling or column stacking

### Modern Table Features

- **Built-in Sorting**: Click column headers to sort
- **Responsive Design**: Automatic column adjustment
- **Professional Styling**: Clean, modern appearance
- **Data Binding**: Direct connection to Power Apps data sources

### Customization Options

- **Table Width**: Adjust Width property for different screen sizes
- **Column Configuration**: Add/remove TableDataField controls
- **Data Source**: Connect to any Power Apps data source
- **Styling**: Modify colors and spacing
- **Actions**: Add row selection and action buttons

### Performance Benefits

- **Efficient Rendering**: Table control optimized for large datasets
- **Virtual Scrolling**: Handles thousands of records smoothly
- **Responsive Loading**: Only renders visible rows
- **Modern Architecture**: Built on latest Power Apps framework

## Table and Form Template

### Overview

A comprehensive master-detail layout combining table list view with form editing capabilities. Features responsive design, CRUD operations, search functionality, and delete confirmation dialogs.

### Structure

```yaml
Screens:
  TableFormScreen:
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
            LayoutGap: =10
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
                  Fill: =App.Theme.Colors.Primary
                  FillPortions: =0
                  Height: =68
                  LayoutAlignItems: =LayoutAlignItems.Center
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutGap: =5
                  PaddingRight: =6
                Children:
                  - Header:
                      Control: Header@0.0.44
            - BodyContainer:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  LayoutDirection: =LayoutDirection.Horizontal
                  LayoutGap: =16
                  PaddingBottom: =2
                  PaddingTop: =4
                Children:
                  - SidebarContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        Fill: =RGBA(255, 255, 255, 1)
                        FillPortions: =If(And(Screen.Size = ScreenSize.Small, Or(newMode, isItemSelected)), 0, 3)
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =10
                        PaddingBottom: =10
                        PaddingLeft: =10
                        PaddingRight: =10
                        PaddingTop: =10
                        Visible: =If(And(Screen.Size = ScreenSize.Small, Or(newMode, isItemSelected)), false, true)
                      Children:
                        - SearchContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              Fill: =RGBA(245, 245, 245, 1)
                              FillPortions: =0
                              Height: =44
                              LayoutDirection: =LayoutDirection.Horizontal
                              PaddingRight: =5
                            Children:
                              - SearchInput:
                                  Control: TextInput@0.0.54
                                  Properties:
                                    FillPortions: =1
                                    Height: =44
                                    Placeholder: ="Search"
                        - AddNewContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              FillPortions: =0
                              Height: =44
                              LayoutDirection: =LayoutDirection.Horizontal
                              Visible: =If(Screen.Size = ScreenSize.Small, true, false)
                            Children:
                              - AddNewButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Transparent
                                    FillPortions: =1
                                    Height: =44
                                    Icon: ="Add"
                                    OnSelect: |
                                      =NewForm(Form);
                                      UpdateContext({ newMode: true })
                                    Text: ="New"
                                    Width: =80
                        - DataTable:
                            Control: Table@1.0.278
                            Properties:
                              EnableRangeSelection: ='PowerAppsOneGrid.EnableRangeSelection'.Enable
                              EnableSorting: ='PowerAppsOneGrid.EnableSorting'.Enable
                              FillPortions: =1
                              Items: =Table()
                              OnSelect: |
                                =UpdateContext({
                                  isItemSelected: true,
                                  newMode: false,
                                  CurrentItem: Table.Selected
                                })
                              ReflowBehavior: ='PowerAppsOneGrid.ReflowBehavior'.ListOnly
                  - RightContainer:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        FillPortions: =7
                        LayoutAlignItems: =LayoutAlignItems.Stretch
                        LayoutDirection: =LayoutDirection.Vertical
                        LayoutGap: =16
                        PaddingBottom: =2
                        PaddingLeft: =2
                        PaddingRight: =2
                        Visible: =If(Or(deleteMode, And(Screen.Size = ScreenSize.Small, !newMode, !isItemSelected)), false, true)
                      Children:
                        - ActionBarContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              Fill: =RGBA(255, 255, 255, 1)
                              FillPortions: =0
                              Height: =60
                              LayoutDirection: =LayoutDirection.Horizontal
                            Children:
                              - BackButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Transparent
                                    Icon: ="ArrowLeft"
                                    Layout: ='ButtonCanvas.Layout'.IconBefore
                                    OnSelect: |
                                      =ResetForm(Form);
                                      UpdateContext({
                                        newMode: false,
                                        editMode: false,
                                        isItemSelected: false
                                      });
                                    Text: ="Back"
                                    Visible: =If(And(Screen.Size = ScreenSize.Small, !deleteMode), true, false)
                                    Width: =75
                              - NewButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Primary
                                    Icon: ="Add"
                                    OnSelect: |
                                      =NewForm(Form);
                                      UpdateContext({ newMode: true })
                                    Text: ="New"
                                    Visible: =If(Screen.Size = ScreenSize.Small, false, And(!newMode, !deleteMode))
                                    Width: =96
                              - EditButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Transparent
                                    Icon: ="Edit"
                                    OnSelect: |
                                      =UpdateContext({
                                        editMode: true,
                                        selectedRecord: Table.Selected
                                      })
                                    Text: ="Edit"
                                    Visible: =And(!newMode, !deleteMode)
                                    Width: =90
                              - DeleteButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Transparent
                                    Icon: ="Delete"
                                    OnSelect: |
                                      =UpdateContext({
                                        deleteMode: true,
                                        selectedRecord: Table.Selected
                                      })
                                    Text: ="Delete"
                                    Visible: =And(!newMode, !deleteMode)
                                    Width: =70
                        - FormContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              Fill: =RGBA(255, 255, 255, 1)
                              LayoutDirection: =LayoutDirection.Vertical
                              LayoutGap: =16
                              LayoutOverflowY: =LayoutOverflow.Scroll
                              PaddingTop: =8
                            Children:
                              - DataForm:
                                  Control: Form@2.4.4
                                  Layout: Vertical
                                  Properties:
                                    BorderStyle: =BorderStyle.None
                                    DataSource: =Applicant
                                    DefaultMode: =If(newMode, FormMode.New, editMode, FormMode.Edit, FormMode.View)
                                    Item: =CurrentItem
                                    NumberOfColumns: =2
                                    OnSuccess: |
                                      =UpdateContext({
                                        CurrentItem: Self.LastSubmit,
                                        isItemSelected: false
                                      });
                                      Notify("Success", NotificationType.Success);
                                      ResetForm(DataForm)
                                  Children:
                                    # Multiple TypedDataCard controls for form fields
                              - ButtonContainer:
                                  Control: GroupContainer@1.3.0
                                  Variant: AutoLayout
                                  Properties:
                                    FillPortions: =0.15
                                    LayoutDirection: =LayoutDirection.Horizontal
                                    LayoutGap: =10
                                    LayoutJustifyContent: =LayoutJustifyContent.End
                                    PaddingRight: =24
                                  Children:
                                    - CancelButton:
                                        Control: Button@0.0.45
                                        Properties:
                                          Appearance: ='ButtonCanvas.Appearance'.Secondary
                                          OnSelect: |
                                            =ResetForm(DataForm);
                                            UpdateContext({
                                              newMode: false,
                                              editMode: false,
                                              isItemSelected: false
                                            });
                                          Text: ="Cancel"
                                    - SubmitButton:
                                        Control: Button@0.0.45
                                        Properties:
                                          Appearance: ='ButtonCanvas.Appearance'.Primary
                                          OnSelect: =SubmitForm(DataForm)
                                          Text: ="Submit"
                  - DeleteConfirmDialog:
                      Control: GroupContainer@1.3.0
                      Variant: AutoLayout
                      Properties:
                        FillPortions: =7
                        LayoutDirection: =LayoutDirection.Vertical
                        Visible: =If(deleteMode, true, false)
                      Children:
                        - ConfirmMessage:
                            Control: Text@0.0.51
                            Properties:
                              Align: ='TextCanvas.Align'.Center
                              Size: =16
                              Text: ="Are you sure you want to delete this record?"
                        - ConfirmButtonContainer:
                            Control: GroupContainer@1.3.0
                            Variant: AutoLayout
                            Properties:
                              LayoutDirection: =LayoutDirection.Horizontal
                              LayoutGap: =15
                              LayoutJustifyContent: =LayoutJustifyContent.Center
                            Children:
                              - ConfirmDeleteButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    OnSelect: |
                                      =Remove(Table(), selectedRecord);
                                      If(IsEmpty(Errors(Table(), selectedRecord)),
                                        UpdateContext({
                                          CurrentItem: First(Table()),
                                          isItemSelected: false,
                                          newMode: false,
                                          deleteMode: false
                                        }));
                                    Text: ="Delete"
                              - CancelDeleteButton:
                                  Control: Button@0.0.45
                                  Properties:
                                    Appearance: ='ButtonCanvas.Appearance'.Secondary
                                    OnSelect: =UpdateContext({ deleteMode: false })
                                    Text: ="Cancel"
```

### Key Features

- **Master-Detail Layout**: Table list (30%) + Form detail (70%)
- **Responsive Design**: Adapts to mobile with conditional visibility
- **CRUD Operations**: Create, Read, Update, Delete functionality
- **Search Functionality**: Built-in search input
- **Delete Confirmation**: Modal dialog for safe deletion
- **Multi-Column Form**: NumberOfColumns=2 for efficient space usage
- **State Management**: Complex context variables for UI states

### State Variables Used

- **newMode**: Creating new record
- **editMode**: Editing existing record
- **deleteMode**: Confirming deletion
- **isItemSelected**: Item selected from table
- **CurrentItem**: Selected record data
- **selectedRecord**: Record to be deleted

### Responsive Behavior

- **Desktop**: Table sidebar + Form detail side by side
- **Mobile**: Full-screen switching between table and form
- **Conditional Visibility**: UI elements show/hide based on screen size and mode

### Form Features

- **Two-Column Layout**: Efficient field arrangement
- **Scrollable Content**: LayoutOverflowY for long forms
- **Dynamic Mode**: New/Edit/View modes based on context
- **Validation**: Built-in form validation and error handling

### Use Cases

- **Admin Panels**: User management, content administration
- **CRM Systems**: Contact management, opportunity tracking
- **Inventory Management**: Product catalog with editing
- **HR Systems**: Employee records management
- **Project Management**: Task and resource management

### Advanced Features

- **Range Selection**: EnableRangeSelection for multi-select
- **Sorting**: EnableSorting for column sorting
- **List-Only Reflow**: ReflowBehavior.ListOnly for mobile optimization
- **Theme Integration**: Uses App.Theme.Colors.Primary

### Customization Options

- **Layout Ratios**: Adjust FillPortions for different sidebar/main ratios
- **Form Columns**: Change NumberOfColumns for field layout
- **Search Logic**: Customize search functionality
- **Action Buttons**: Add/remove CRUD operations
- **Validation Rules**: Implement custom form validation

## Scrollable Template

### Overview

A simple scrollable layout with fixed header bar and flexible content area using FluidGrid. Perfect for content that needs to scroll while keeping navigation elements fixed at the top.

### Structure

```yaml
Screens:
  ScrollableScreen:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - QuickActionBar:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(56, 96, 178, 1)
            Height: =88
            Width: =Parent.Width
      - AppTitle:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(255, 255, 255, 1)
            Font: =Font.'Open Sans'
            Height: =88
            Size: =18
            Text: ="[Title]"
            Width: =Parent.Width
      - ScrollableCanvas:
          Control: FluidGrid@2.3.0
          Properties:
            BorderThickness: =0
            Height: =Parent.Height - Self.Y
            Width: =Parent.Width
            Y: =QuickActionBar.Y + QuickActionBar.Height
          Children:
            - ContentCard:
                Control: DataCard@1.0.2
                Properties:
                  Height: =Parent.Height - 100
                  Width: =Parent.Width
                  X: =0
                  Y: =0
```

### Key Features

- **Fixed Header**: Rectangle with colored background (88px height)
- **Overlay Title**: Label positioned over the header rectangle
- **FluidGrid Container**: Scrollable content area below header
- **Full-Width Layout**: All elements span Parent.Width
- **Dynamic Height**: Content area calculates height based on header

### Layout Structure

1. **QuickActionBar**: Fixed header rectangle with brand color
2. **AppTitle**: Centered title text overlaying the header
3. **ScrollableCanvas**: FluidGrid for scrollable content
4. **ContentCard**: DataCard container for actual content

### Positioning Logic

- **Header**: Fixed at top (Y=0, Height=88)
- **Title**: Same position as header for overlay effect
- **Canvas**: Starts after header (Y = Header.Y + Header.Height)
- **Content**: Fills canvas with 100px bottom margin

### Use Cases

- **Content Pages**: Articles, documentation, long-form content
- **Settings Screens**: Long lists of configuration options
- **Feed Layouts**: Social media feeds, news articles
- **Product Catalogs**: Scrollable product listings
- **Dashboard Content**: Metrics and charts that need scrolling

### FluidGrid Benefits

- **Smooth Scrolling**: Native scrolling performance
- **Responsive**: Adapts to different screen sizes
- **Touch-Friendly**: Optimized for mobile interactions
- **Memory Efficient**: Only renders visible content

### Header Design

- **Brand Colors**: Uses primary blue (RGBA(56, 96, 178, 1))
- **Border Accent**: Darker blue border (RGBA(0, 18, 107, 1))
- **White Text**: High contrast for readability
- **Centered Title**: Professional appearance

### Content Area

- **DataCard Container**: Flexible content wrapper
- **Full Width**: Spans entire screen width
- **Calculated Height**: Parent.Height - 100 for bottom spacing
- **Positioned at Origin**: X=0, Y=0 within FluidGrid

### Responsive Features

- **Width Scaling**: All elements use Parent.Width
- **Height Adaptation**: Content area adjusts to screen height
- **Touch Scrolling**: Native mobile scroll behavior
- **Overflow Handling**: Content scrolls when exceeding screen height

### Customization Options

- **Header Height**: Adjust Height property for taller/shorter headers
- **Header Colors**: Modify Fill and BorderColor for different themes
- **Title Styling**: Change Font, Size, and Color properties
- **Content Margins**: Adjust Height calculation for different spacing
- **Border Styling**: Modify BorderThickness and BorderColor

### Performance Considerations

- **Lightweight**: Minimal control hierarchy
- **Efficient Scrolling**: FluidGrid optimized for performance
- **Memory Usage**: DataCard only loads visible content
- **Smooth Animations**: Native scroll animations

### Alternative Uses

- **Mobile-First**: Perfect for mobile app layouts
- **Simple Layouts**: When complex containers aren't needed
- **Legacy Support**: Compatible with older Power Apps versions
- **Quick Prototypes**: Fast setup for content-heavy screens

## List Template

### Overview

A classic mobile-style list layout with fixed header and gallery using BrowseLayout variant. Features image thumbnails, title/subtitle text, and selection indicators with chevron navigation.

### Structure

```yaml
Screens:
  ListScreen:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - QuickActionBar:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(56, 96, 178, 1)
            Height: =64
            Width: =Parent.Width
      - AppTitle:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            BorderColor: =RGBA(0, 0, 0, 1)
            Color: =RGBA(255, 255, 255, 1)
            Font: =Font.'Open Sans'
            Height: =64
            PaddingRight: =10
            Size: =18
            Text: ="App name"
            Width: =Parent.Width
      - ItemGallery:
          Control: Gallery@2.15.0
          Variant: BrowseLayout_Vertical_TwoTextOneImageVariant_ver5.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Items: =Applicant
            Width: =Parent.Width
            Y: =64
          Children:
            - ItemImage:
                Control: Image@2.2.3
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Height: =72
                  OnSelect: =Select(Parent)
                  RadiusBottomLeft: =8
                  RadiusBottomRight: =8
                  RadiusTopLeft: =8
                  RadiusTopRight: =8
                  Width: =72
                  X: =16
                  Y: =(Parent.TemplateHeight / 2) - (Self.Height / 2)
            - ItemTitle:
                Control: Label@2.5.1
                Properties:
                  BorderColor: =RGBA(0, 0, 0, 1)
                  Color: =RGBA(50, 49, 48, 1)
                  Font: =Font.'Open Sans'
                  FontWeight: =If(ThisItem.IsSelected, FontWeight.Semibold, FontWeight.Normal)
                  Height: =Self.Size * 1.8
                  OnSelect: =Select(Parent)
                  Size: =14
                  Text: =ThisItem.SampleHeading
                  VerticalAlign: =VerticalAlign.Top
                  Width: =Parent.TemplateWidth - 173
                  X: =103
                  Y: =(Parent.TemplateHeight - (Self.Size * 1.8 + ItemSubtitle.Size * 1.8)) / 2
            - ItemSubtitle:
                Control: Label@2.5.1
                Properties:
                  BorderColor: =RGBA(0, 0, 0, 1)
                  Font: =Font.'Open Sans'
                  FontWeight: =If(ThisItem.IsSelected, FontWeight.Semibold, FontWeight.Normal)
                  Height: =Self.Size * 1.8
                  OnSelect: =Select(Parent)
                  Size: =12
                  Text: =ThisItem.SampleText
                  VerticalAlign: =VerticalAlign.Top
                  Width: =ItemTitle.Width
                  X: =ItemTitle.X
                  Y: =ItemTitle.Y + ItemTitle.Height
            - NavigationArrow:
                Control: Classic/Icon@2.5.0
                Properties:
                  AccessibleLabel: =Self.Tooltip
                  BorderColor: =RGBA(0, 0, 0, 1)
                  Color: =RGBA(166, 166, 166, 1)
                  DisabledBorderColor: =RGBA(56, 56, 56, 1)
                  DisabledColor: =RGBA(119, 119, 119, 1)
                  Height: =50
                  Icon: =Icon.ChevronRight
                  OnSelect: =Select(Parent)
                  PaddingBottom: =16
                  PaddingLeft: =16
                  PaddingRight: =16
                  PaddingTop: =16
                  Tooltip: ="View item details"
                  Width: =50
                  X: =Parent.TemplateWidth - Self.Width - 12
                  Y: =(Parent.TemplateHeight / 2) - (Self.Height / 2)
            - ItemSeparator:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(255, 255, 255, 1)
                  Height: =8
                  OnSelect: =Select(Parent)
                  Width: =Parent.TemplateWidth
                  Y: =Parent.TemplateHeight - Self.Height
            - SelectionIndicator:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(0, 18, 107, 1)
                  Height: =Parent.TemplateHeight - ItemSeparator.Height
                  OnSelect: =Select(Parent)
                  Visible: =ThisItem.IsSelected
                  Width: =4
```

### Key Features

- **BrowseLayout Variant**: Uses BrowseLayout_Vertical_TwoTextOneImageVariant_ver5.0
- **Fixed Header**: 64px height header with app title
- **Image Thumbnails**: 72x72px rounded images with 8px radius
- **Two-Text Layout**: Title (14px) and subtitle (12px) text
- **Selection States**: FontWeight changes based on IsSelected
- **Navigation Arrow**: ChevronRight icon for detail navigation
- **Selection Indicator**: 4px blue bar on selected items
- **Item Separators**: White separator bars between items

### Layout Structure

1. **QuickActionBar**: Fixed header rectangle (64px)
2. **AppTitle**: Centered title overlaying header
3. **ItemGallery**: Scrollable list taking remaining height
4. **Gallery Items**: Image + Title + Subtitle + Arrow + Indicators

### Item Layout (per gallery item)

- **Image**: Left-aligned (X=16), vertically centered, 72x72px
- **Title**: Positioned after image (X=103), calculated vertical centering
- **Subtitle**: Below title, same X position
- **Arrow**: Right-aligned (X=TemplateWidth-62), vertically centered
- **Separator**: Bottom of item, full width, 8px height
- **Selection Bar**: Left edge, 4px width, visible when selected

### Positioning Calculations

- **Image Y**: `(Parent.TemplateHeight / 2) - (Self.Height / 2)`
- **Text Y**: `(Parent.TemplateHeight - (Title.Height + Subtitle.Height)) / 2`
- **Arrow Y**: `(Parent.TemplateHeight / 2) - (Self.Height / 2)`
- **Text Width**: `Parent.TemplateWidth - 173` (accounts for image + arrow + margins)

### Use Cases

- **Contact Lists**: People directory with photos
- **Product Catalogs**: Items with images and descriptions
- **News Feeds**: Articles with thumbnails
- **File Browsers**: Documents with icons and metadata
- **Social Media**: Posts with profile pictures
- **Settings Menus**: Configuration options with icons

### Visual Design

- **Brand Colors**: Primary blue header and selection indicators
- **Typography**: Open Sans font with size hierarchy (18/14/12)
- **Selection Feedback**: Bold text and blue indicator bar
- **Touch Targets**: Proper spacing and padding for mobile
- **Visual Hierarchy**: Clear information hierarchy with image/text/action

### Responsive Features

- **Full Width**: All elements scale with Parent.Width
- **Dynamic Height**: Gallery fills remaining screen space
- **Touch-Friendly**: Large touch targets and proper spacing
- **Scroll Performance**: Optimized gallery for smooth scrolling

### Interaction Patterns

- **Item Selection**: Tap anywhere on item to select
- **Navigation**: Chevron arrow indicates detail view available
- **Visual Feedback**: Selected state with bold text and indicator
- **Accessibility**: Proper AccessibleLabel and Tooltip properties

### Customization Options

- **Header Height**: Adjust Height property for different header sizes
- **Item Height**: Modify TemplateHeight for taller/shorter items
- **Image Size**: Change Width/Height for different thumbnail sizes
- **Colors**: Modify Fill and BorderColor for different themes
- **Typography**: Adjust Size and FontWeight for different text styles
- **Spacing**: Modify X/Y positions and margins for different layouts

### Performance Considerations

- **Gallery Optimization**: Uses efficient BrowseLayout variant
- **Image Loading**: Optimized image control for thumbnails
- **Selection State**: Efficient IsSelected property binding
- **Scroll Performance**: Smooth scrolling with proper item sizing

## Success Template

### Overview

A clean success confirmation screen with centered circular icon and message. Perfect for showing completion states, confirmations, and positive feedback to users.

### Structure

```yaml
Screens:
  SuccessScreen:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - SuccessCircle:
          Control: Circle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(56, 96, 178, 1)
            X: =Parent.Width/2 - Self.Width/2
            Y: =(Parent.Height/2 - Self.Height/2) * .7
      - SuccessIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Color: =RGBA(255, 255, 255, 1)
            Height: =SuccessCircle.Height
            Icon: =Icon.Check
            PaddingBottom: =Self.PaddingTop
            PaddingLeft: =Self.PaddingTop
            PaddingRight: =Self.PaddingTop
            PaddingTop: =24
            PressedFill: =RGBA(255, 255, 255, 0.3)
            Width: =SuccessCircle.Width
            X: =Parent.Width/2 - Self.Width/2
            Y: =(Parent.Height/2 - Self.Height/2) * .7
      - SuccessMessage:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            AutoHeight: =true
            BorderColor: =RGBA(0, 0, 0, 1)
            Font: =Font.'Open Sans'
            Height: =SuccessCircle.Height
            Size: =20
            Text: ="This was successfully completed"
            Width: =Parent.Width * 0.75
            X: =Parent.Width/2 - Self.Width/2
            Y: =SuccessIcon.Y + SuccessIcon.Height + 100
```

### Key Features

- **Centered Layout**: All elements centered horizontally using Parent.Width/2 calculations
- **Layered Design**: Circle background with overlaid check icon
- **Vertical Positioning**: Icon positioned at 70% of center height (\*.7)
- **Responsive Sizing**: Message width is 75% of parent width
- **Consistent Spacing**: 100px gap between icon and message
- **Brand Colors**: Primary blue circle with white check icon

### Layout Structure

1. **SuccessCircle**: Blue circular background
2. **SuccessIcon**: White check mark overlaid on circle
3. **SuccessMessage**: Centered text below the icon

### Positioning Logic

- **Horizontal Centering**: `X: =Parent.Width/2 - Self.Width/2`
- **Vertical Positioning**: `Y: =(Parent.Height/2 - Self.Height/2) * .7`
- **Icon Overlay**: Same X/Y as circle for perfect alignment
- **Message Spacing**: `Y: =SuccessIcon.Y + SuccessIcon.Height + 100`

### Use Cases

- **Form Submissions**: Confirmation after successful form submission
- **Payment Processing**: Success after payment completion
- **Account Creation**: Welcome message after registration
- **Task Completion**: Confirmation of completed actions
- **Data Sync**: Success after data synchronization
- **Settings Updates**: Confirmation of saved preferences

### Customization Options

- **Icon Type**: Change Icon property (Icon.Check, Icon.Accept, Icon.Checkmark)
- **Colors**: Modify Fill and Color for different themes
- **Message Text**: Update Text property for specific confirmations
- **Positioning**: Adjust Y multiplier (.7) for different vertical positions
- **Sizing**: Modify Width/Height for larger/smaller icons
- **Spacing**: Change the 100px gap for tighter/looser layout

## Calendar Template

### Overview

A comprehensive calendar interface with Office 365 integration featuring month navigation, event display, and calendar selection. Includes a full calendar grid view with event indicators and a detailed event list for selected dates.

### Structure

```yaml
Screens:
  CalendarScreen:
    Properties:
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
    Children:
      - RectMeetingBkg2:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(240, 240, 240, 1)
            Height: =42
            Visible: =_calendarVisible
            Width: =Parent.Width - Self.X
            X: =422
            Y: =RectQuickActionBar7.Height
      - RectQuickActionBar7:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(56, 96, 178, 1)
            Height: =64
            Width: =Parent.Width
          Children:
            - LblAppName6:
                Control: Label@2.5.1
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Font: =Font.'Open Sans'
                  Height: =64
                  Size: =18
                  Text: ="Calendar"
                  Width: =Parent.Width - Self.X * 2
                  X: =32
            - LblResetToday2:
                Control: Label@2.5.1
                Properties:
                  Align: =Align.Center
                  Color: =iconCalendar2.Color
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Bold
                  Height: =iconCalendar2.Height
                  PaddingTop: =12
                  Size: =11
                  Text: =DateDiff(Date(Year(Today()), Month(Today()), 1), Today(), TimeUnit.Days) + 1
                  Width: =iconCalendar2.Width
                  X: =iconCalendar2.X
                  Y: =iconCalendar2.Y
            - iconCalendar2:
                Control: Classic/Icon@2.5.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Color: =RGBA(0, 18, 107, 1)
                  Height: =40
                  Icon: =Icon.CalendarBlank
                  OnSelect: |
                    =/*resets calendar view and date selection to today*/
                    Set(_dateSelected, Today());
                    Set(_firstDayOfMonth, DateAdd(Today(), 1 - Day(Today()), TimeUnit.Days));
                    Set(_firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 2 + 1), TimeUnit.Days));
                    Set(_lastDayOfMonth, DateAdd(DateAdd(_firstDayOfMonth, 1, TimeUnit.Months), -1, TimeUnit.Days))
                  Tooltip: ="Reset selected date to today"
                  Width: =40
                  X: =395 - Self.Width
                  Y: =dropdownCalendarSelection2.Y
            - dropdownCalendarSelection2:
                Control: Classic/DropDown@2.3.1
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  ChevronBackground: =RGBA(56, 96, 178, 1)
                  ChevronFill: =RGBA(255, 255, 255, 1)
                  Default: =_myCalendar.DisplayName
                  Font: =Font.'Open Sans'
                  Items: =Office365Outlook_3.CalendarGetTables().value
                  Items.Value: =DisplayName
                  OnSelect: |
                    =/*retrieves calendar events for all days in current month view and selected calendar*/
                    Set(_calendarVisible, false);
                    UpdateContext({_showLoading: true});
                    Set(_myCalendar, Self.Selected);
                    Set(_minDate, DateAdd(_firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 2 + 1), TimeUnit.Days));
                    Set(_maxDate, DateAdd(DateAdd(_firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 2 + 1), TimeUnit.Days), 40, TimeUnit.Days));
                    ClearCollect(MyCalendarEvents, Office365Outlook_3.GetEventsCalendarViewV2(_myCalendar.Name, Text(_minDate, DateTimeFormat.UTC), Text(_maxDate, DateTimeFormat.UTC)).value);
                    UpdateContext({_showLoading: false});
                    Set(_calendarVisible, true)
                  Tooltip: ="Select a calendar"
                  Width: =307
                  X: =32
                  Y: =RectQuickActionBar7.Height + 24
      - LblMonthSelected2:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            Font: =Font.'Open Sans'
            Height: =50
            Size: =18
            Text: =Text(_firstDayOfMonth, "mmmm yyyy")
            Visible: =_calendarVisible
            Width: =419
            Y: =dropdownCalendarSelection2.Y + dropdownCalendarSelection2.Height + 40
      - iconPrevMonth2:
          Control: Classic/Icon@2.5.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Color: =RGBA(0, 18, 107, 1)
            Height: =50
            Icon: =Icon.ChevronLeft
            OnSelect: |
              =/*changes month view to previous month*/
              Set(_firstDayOfMonth, DateAdd(_firstDayOfMonth, -1, TimeUnit.Months));
              Set(_firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 2 + 1), TimeUnit.Days));
              Set(_lastDayOfMonth, DateAdd(DateAdd(_firstDayOfMonth, 1, TimeUnit.Months), -1, TimeUnit.Days));
              /*collects calendar events for all days in current month view*/
              If(_minDate > _firstDayOfMonth, 
                Set(_minDate, _firstDayOfMonth); 
                Collect(MyCalendarEvents, Office365Outlook_3.GetEventsCalendarViewV2(_myCalendar.Name, Text(_minDate, DateTimeFormat.UTC), Text(_lastDayOfMonth, DateTimeFormat.UTC)).value)
              )
            Tooltip: ="View previous month"
            Visible: =_calendarVisible
            Width: =59
            Y: =LblMonthSelected2.Y
      - iconNextMonth2:
          Control: Classic/Icon@2.5.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Color: =RGBA(0, 18, 107, 1)
            Height: =50
            Icon: =Icon.ChevronRight
            OnSelect: |
              =/*changes month view to next month*/
              Set(_firstDayOfMonth, DateAdd(_firstDayOfMonth, 1, TimeUnit.Months));
              Set(_firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 2 + 1), TimeUnit.Days));
              Set(_lastDayOfMonth, DateAdd(DateAdd(_firstDayOfMonth, 1, TimeUnit.Months), -1, TimeUnit.Days));
              /*collects calendar events for all days in current month view*/
              If(_lastDayOfMonth > _maxDate, 
                Set(_maxDate, _lastDayOfMonth); 
                Collect(MyCalendarEvents, Office365Outlook_3.GetEventsCalendarViewV2(_myCalendar.Name, Text(_firstDayOfMonth, DateTimeFormat.UTC), Text(_maxDate, DateTimeFormat.UTC)).value)
              )
            Tooltip: ="View next month"
            Visible: =_calendarVisible
            Width: =59
            X: =419 - Self.Width
            Y: =LblMonthSelected2.Y
      - WeekdayGallery2:
          Control: Gallery@2.15.0
          Variant: WeekdayGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =45
            Items: =Calendar.WeekdaysShort()
            TemplatePadding: =0
            Visible: =_calendarVisible
            Width: =420
            Y: =LblMonthSelected2.Y + LblMonthSelected2.Height + 10
          Children:
            - Title15:
                Control: Label@2.5.1
                Properties:
                  Align: =Align.Center
                  Font: =Font.'Open Sans'
                  Height: =WeekdayGallery2.TemplateHeight
                  Size: =17 * WeekdayGallery2.TemplateWidth / 77
                  Text: =ThisItem.Value
                  Width: =WeekdayGallery2.TemplateWidth
                  X: =WeekdayGallery2.TemplateWidth / 2 - Self.Width / 2
                  Y: =WeekdayGallery2.TemplateHeight / 2 - Self.Height / 2
      - MonthDayGallery2:
          Control: Gallery@2.15.0
          Variant: MonthDayGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =425
            Items: =[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]
            TemplatePadding: =0
            TemplateSize: =60
            Visible: =_calendarVisible
            Width: =420
            Y: =WeekdayGallery2.Y + WeekdayGallery2.Height
          Children:
            - Circle3:
                Control: Circle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(186, 202, 226, 1)
                  Height: =Self.Width
                  Visible: |
                    =/*Visible if calendar events are found on this day*/
                    CountRows(Filter(MyCalendarEvents, DateValue(Text(Start)) = DateAdd(_firstDayInView,ThisItem.Value, TimeUnit.Days))) > 0 && !Subcircle2.Visible && Title16.Visible
                  Width: =6.5
                  X: =MonthDayGallery2.TemplateWidth / 2 - Self.Width / 2
                  Y: =MonthDayGallery2.TemplateHeight * (0.75)
            - Subcircle2:
                Control: Circle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(56, 96, 178, 1)
                  Height: =3 * Title16.Size
                  Visible: =And(DateAdd(_firstDayInView, ThisItem.Value) = _dateSelected, Title16.Visible)
                  Width: =Self.Height
                  X: =MonthDayGallery2.TemplateWidth/2 - Self.Width/2
                  Y: =MonthDayGallery2.TemplateHeight / 2 - Self.Height / 2
            - Title16:
                Control: Label@2.5.1
                Properties:
                  Align: =Align.Center
                  Color: |
                    =If(DateAdd(_firstDayInView, ThisItem.Value) = _dateSelected, RGBA(255, 255, 255, 1), 
                       DateAdd(_firstDayInView, ThisItem.Value) = Today(), RGBA(47, 41, 43, 1), 
                       LblMonthSelected2.Color)
                  Fill: |
                    =/*Fill value changes if the gallery item day = today, or if it lies outside of the current month*/
                    If(/*Date selected is today*/
                       DateAdd(_firstDayInView, ThisItem.Value) = Today() && DateAdd(_firstDayInView, ThisItem.Value) = _dateSelected, RGBA(0,0,0,0),
                       /*Today when it is not selected*/
                       DateAdd(_firstDayInView, ThisItem.Value) = Today(), ColorFade(Subcircle2.Fill, 0.67), 
                       /*The day is outside the range of the currently selected month*/
                       Abs(Self.Text - ThisItem.Value) > 10,RGBA(200, 200, 200, 0.3), 
                       RGBA(0, 0, 0, 0))
                  Font: =Font.'Open Sans'
                  Height: =MonthDayGallery2.TemplateHeight
                  OnSelect: =Set(_dateSelected, DateAdd(_firstDayInView, ThisItem.Value, TimeUnit.Days))
                  Size: =17 * MonthDayGallery2.TemplateWidth / 91
                  Text: =Day(DateAdd(_firstDayInView,ThisItem.Value, TimeUnit.Days))
                  Visible: |
                    =/*This item is in a row containing no days of the visible month*/
                    !(DateAdd(_firstDayInView,ThisItem.Value, TimeUnit.Days) - Weekday(DateAdd(_firstDayInView,ThisItem.Value, TimeUnit.Days)) + 1 > _lastDayOfMonth)
                  Width: =MonthDayGallery2.TemplateWidth
      - LblDateSelected2:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =RectMeetingBkg2.Height
            Text: =Text(_dateSelected, DateTimeFormat.LongDate)
            Visible: =_calendarVisible
            Width: =Parent.Width / 3 - 60
            X: =451
            Y: =RectQuickActionBar7.Height
      - CalendarEventsGallery2:
          Control: Gallery@2.15.0
          Variant: CalendarEventsGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Items: |
              =/*Shows events only on selected date*/
              SortByColumns(Filter(MyCalendarEvents, Text(Start, DateTimeFormat.ShortDate) = Text(_dateSelected, DateTimeFormat.ShortDate)), "Start")
            TemplatePadding: =0
            Visible: =_calendarVisible
            Width: =Parent.Width - Self.X
            X: =422
            Y: =LblDateSelected2.Y + LblDateSelected2.Height
          Children:
            - Rectangle11:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  BorderThickness: =If(ThisItem.Id = _selectedCalendarEvent.Id, 2, 0)
                  Fill: =RGBA(0,0,0,0)
                  Height: =Parent.TemplateHeight
                  Width: =Parent.TemplateWidth
            - Title17:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Semibold
                  Height: =Self.Size * 1.8
                  OnSelect: =Set(_selectedCalendarEvent, ThisItem)
                  Size: =19 * CalendarEventsGallery2.TemplateHeight / 105
                  Text: =ThisItem.Subject
                  Tooltip: =ThisItem.Subject
                  Width: =CalendarEventsGallery2.TemplateWidth - Self.X - 10
                  X: =Body3.X + Body3.Width + 10
                  Y: =CalendarEventsGallery2.TemplateHeight / 4 - Self.Height / 2 + 5
            - Body3:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  Height: =Title17.Height
                  Size: =17 * CalendarEventsGallery2.TemplateHeight / 105
                  Text: =Text(ThisItem.Start, DateTimeFormat.ShortTime)
                  Width: =110
                  X: =32
                  Y: =Title17.Y
            - Subtitle8:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Lighter
                  Height: =Self.Size * 2
                  Size: =18 * CalendarEventsGallery2.TemplateHeight / 105
                  Text: =ThisItem.Location
                  Tooltip: =ThisItem.Location
                  Width: =CalendarEventsGallery2.TemplateWidth - Self.X - 10
                  X: =iconLocation2.X + iconLocation2.Width + 10
                  Y: =3 / 4 * CalendarEventsGallery2.TemplateHeight - Self.Height / 2 - 5
            - iconLocation2:
                Control: Classic/Icon@2.5.0
                Properties:
                  Color: =RGBA(0, 18, 107, 1)
                  Height: =Subtitle8.Height
                  Icon: =Icon.Waypoint
                  Width: =28
                  X: =Title17.X
                  Y: =Subtitle8.Y
            - Description2:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  Height: =Subtitle8.Height
                  Size: =17 * CalendarEventsGallery2.TemplateHeight / 105
                  Text: =DateDiff(ThisItem.Start, ThisItem.End, TimeUnit.Minutes) & Lower(Left("Minute_Name", 1))
                  Width: =100
                  X: =32
                  Y: =Subtitle8.Y
            - Separator13:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(0, 18, 107, 1)
                  Height: =1
                  Width: =Parent.TemplateWidth
                  Y: =Parent.TemplateHeight - 1
      - iconEmptyState3:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            DisplayMode: =DisplayMode.View
            Icon: =Icon.CalendarBlank
            Visible: =IsBlank(_userDomain)
            X: =2* Parent.Width/3 - Self.Width / 2
            Y: =LblNoEvents2.Y - Self.Height
      - LblNoEvents2:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            DisplayMode: =DisplayMode.View
            Font: =Font.'Open Sans'
            Height: =220
            Size: =15
            Text: |
              =If(IsBlank(_userDomain), "Select a calendar from the drop down to begin", 
                 _showLoading, "Loading events...", 
                 "No events scheduled")
            Visible: =IsBlank(_userDomain) || _showLoading || And(CountRows(CalendarEventsGallery2.AllItems) = 0 && _calendarVisible)
            Width: =600
            X: =2* Parent.Width/3 - Self.Width / 2
            Y: =CalendarEventsGallery2.Y + CalendarEventsGallery2.Height/2 - Self.Height/2
      - RectCalendarSeparator2:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Width: =2
            X: =420
            Y: =RectQuickActionBar7.Height
```

### Key Features

- **Office 365 Integration**: Connects to Office365Outlook_3 connector
- **Calendar Selection**: Dropdown to choose from available calendars
- **Month Navigation**: Previous/next month with chevron icons
- **Calendar Grid**: 7x6 grid showing full month view with surrounding dates
- **Event Indicators**: Visual dots on dates with events
- **Date Selection**: Click any date to view events
- **Event List**: Detailed event display with time, location, duration
- **Today Reset**: Quick button to return to current date
- **Loading States**: Shows loading spinner during data fetch
- **Empty States**: Helpful messages when no calendar selected or no events

### Calendar Variables Used

- **_calendarVisible**: Controls calendar visibility during loading
- **_dateSelected**: Currently selected date
- **_firstDayOfMonth**: First day of current month view
- **_firstDayInView**: First date shown in calendar grid (may be previous month)
- **_lastDayOfMonth**: Last day of current month
- **_myCalendar**: Selected calendar from dropdown
- **_minDate/_maxDate**: Date range markers to prevent duplicate API calls
- **_selectedCalendarEvent**: Currently selected event in list
- **_showLoading**: Loading state indicator
- **_userDomain**: User's email domain for initialization

### Office 365 API Calls

- **CalendarGetTables()**: Retrieves available calendars
- **GetEventsCalendarViewV2()**: Fetches events for date range
- **MyCalendarEvents**: Collection storing fetched events

### Calendar Grid Logic

- **42 Items**: Gallery with items [0-41] for 6 weeks × 7 days
- **Date Calculation**: `DateAdd(_firstDayInView, ThisItem.Value, TimeUnit.Days)`
- **Event Indicators**: Circle3 shows when events exist on date
- **Selection Indicator**: Subcircle2 highlights selected date
- **Today Highlighting**: Special styling for current date
- **Month Boundaries**: Faded styling for dates outside current month

### Event Display Features

- **Time Display**: Start time in short format
- **Duration**: Calculated minutes between start/end
- **Location**: With waypoint icon
- **Subject**: Event title with tooltip
- **Selection**: Border highlight for selected event
- **Sorting**: Events sorted by start time

### Use Cases

- **Meeting Schedulers**: View and select meeting times
- **Event Planning**: See availability and existing events
- **Calendar Integration**: Embed calendar view in business apps
- **Appointment Booking**: Show available/busy times
- **Team Calendars**: Shared calendar viewing

### Responsive Design

- **Fixed Layout**: Calendar grid maintains consistent 420px width
- **Split View**: Calendar (420px) + Events (remaining width)
- **Vertical Separator**: 2px line dividing calendar and events
- **Header Bar**: Full-width header with controls

### Customization Options

- **Colors**: Modify RGBA values for brand consistency
- **Calendar Size**: Adjust TemplateSize and grid dimensions
- **Event Fields**: Add/remove event properties displayed
- **Date Formats**: Change date display formats
- **Loading Messages**: Customize empty state text
- **Icons**: Replace calendar and navigation icons#
# Landscape Print Template

### Overview

A specialized print layout template designed for landscape orientation printing. Features fixed dimensions optimized for landscape paper size (1123x794) with a print button that hides during the actual printing process.

### Structure

```yaml
Screens:
  LandscapePrintScreen:
    Properties:
      Height: =794
      LoadingSpinnerColor: =RGBA(56, 96, 178, 1)
      Width: =1123
    Children:
      - PrintContainer2:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            Height: =68
            LayoutAlignItems: =LayoutAlignItems.Center
            LayoutDirection: =LayoutDirection.Horizontal
            LayoutJustifyContent: =LayoutJustifyContent.End
            PaddingRight: =20
            Width: =1123
          Children:
            - PrintButton2:
                Control: Button@0.0.45
                Properties:
                  Appearance: ='ButtonCanvas.Appearance'.Secondary
                  OnSelect: =Print()
                  Text: ="Print"
                  Visible: =Not(Screen24.Printing)
                  X: =72
                  Y: =272
```

### Key Features

- **Fixed Landscape Dimensions**: 1123x794 pixels (standard landscape paper ratio)
- **Print Functionality**: Built-in Print() function on button click
- **Smart Button Visibility**: Print button hides during printing process using `Not(Screen24.Printing)`
- **Right-Aligned Controls**: Print button positioned at the end of the container
- **Minimal Layout**: Clean, focused design for print output

### Print-Specific Properties

- **Screen Dimensions**: Fixed width/height for consistent print layout
- **Print Detection**: Uses `Screen24.Printing` property to detect print state
- **Print Function**: `Print()` function triggers the print dialog
- **Button Visibility**: `Visible: =Not(Screen24.Printing)` hides UI during print

### Layout Structure

1. **Screen**: Fixed landscape dimensions (1123x794)
2. **PrintContainer2**: Horizontal container for print controls
3. **PrintButton2**: Secondary button that triggers printing

### Print Behavior

- **Before Print**: Button is visible and clickable
- **During Print**: Button automatically hides (`Screen24.Printing` = true)
- **After Print**: Button becomes visible again
- **Print Output**: Only the content area prints, not the button

### Use Cases

- **Reports**: Landscape-oriented business reports
- **Charts/Graphs**: Wide data visualizations that need landscape format
- **Certificates**: Landscape certificates or awards
- **Invoices**: Wide invoices with multiple columns
- **Dashboards**: Print-friendly dashboard snapshots
- **Forms**: Wide forms that benefit from landscape layout

### Responsive Design

- **Fixed Layout**: Maintains exact dimensions for consistent print output
- **Print-Optimized**: Designed specifically for paper output, not screen viewing
- **Button Positioning**: Right-aligned for easy access without interfering with content

### Customization Options

- **Paper Size**: Adjust Width/Height for different paper formats (A4, Letter, Legal)
- **Content Area**: Add content containers below the print controls
- **Print Settings**: Customize Print() function with specific parameters
- **Button Styling**: Modify Appearance and positioning
- **Multiple Buttons**: Add additional print options (PDF, different formats)

### Print Integration

```powerfx
// Basic print function
OnSelect: =Print()

// Print with specific settings (if supported)
OnSelect: =Print(Screen24)

// Conditional printing based on data
OnSelect: =If(IsBlank(DataSource), 
    Notify("No data to print", NotificationType.Warning),
    Print()
)
```

### Best Practices

- **Content Layout**: Design content to fit within printable area margins
- **Font Sizes**: Use print-friendly font sizes (10pt minimum)
- **Color Considerations**: Ensure content prints well in black and white
- **Page Breaks**: Consider where natural page breaks should occur
- **Print Preview**: Test print output before finalizing layout