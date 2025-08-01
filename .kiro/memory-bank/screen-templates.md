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
4. **StarVisible**: Required field indicator (*)

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