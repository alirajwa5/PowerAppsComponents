# Utility Templates

## Scrollable Template

### Overview
A simple scrollable layout with fixed header bar and flexible content area using FluidGrid. Perfect for content that needs to scroll while keeping navigation elements fixed at the top.

### Key Features
- Fixed header with Rectangle + Label overlay
- FluidGrid@2.3.0 for smooth scrollable content
- Dynamic height calculation (Parent.Height - Self.Y)
- DataCard@1.0.2 as content container

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

### Use Cases
- Content pages, Settings screens, Feed layouts, Product catalogs, Dashboard content

## Success Template

### Overview
A clean success confirmation screen with centered circular icon and message. Perfect for showing completion states, confirmations, and positive feedback to users.

### Key Features
- Centered layout using Parent.Width/2 calculations
- Layered design with Circle background and overlaid check icon
- Vertical positioning at 70% of center height (*.7)
- Responsive message width (75% of parent)

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
            Width: =SuccessCircle.Width
            X: =Parent.Width/2 - Self.Width/2
            Y: =(Parent.Height/2 - Self.Height/2) * .7
      - SuccessMessage:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            AutoHeight: =true
            Font: =Font.'Open Sans'
            Size: =20
            Text: ="This was successfully completed"
            Width: =Parent.Width * 0.75
            X: =Parent.Width/2 - Self.Width/2
            Y: =SuccessIcon.Y + SuccessIcon.Height + 100
```

### Positioning Logic
- **Horizontal Centering**: `X: =Parent.Width/2 - Self.Width/2`
- **Vertical Positioning**: `Y: =(Parent.Height/2 - Self.Height/2) * .7`
- **Icon Overlay**: Same X/Y as circle for perfect alignment
- **Message Spacing**: `Y: =SuccessIcon.Y + SuccessIcon.Height + 100`

### Use Cases
- Form submissions, Payment processing, Account creation, Task completion, Data sync, Settings updates

### Alternative Icons
- Icon.Accept, Icon.Checkmark, Icon.CompletedSolid, Icon.Trophy, Icon.Like

## Tutorial Template

### Overview
Same structure as Success Template but can be used for onboarding, tutorials, or instructional screens. Uses the same centered icon and message pattern.

### Use Cases
- Onboarding screens, Tutorial steps, Help instructions, Feature introductions, Getting started guides
## Email Te
mplate

### Overview
A comprehensive email composition screen with recipient selection, search functionality, and Office 365 integration. Features people picker, subject/message fields, and send functionality.

### Key Features
- Office 365 integration with Office365Users.SearchUser and Office365Outlook.SendEmail
- Dynamic people picker with search and selection
- Email validation and recipient management
- Multi-line message input with proper sizing
- Send button with validation (disabled until requirements met)

### Structure
```yaml
Screens:
  EmailScreen:
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
            Color: =RGBA(255, 255, 255, 1)
            Font: =Font.'Open Sans'
            Height: =64
            Size: =18
            Text: ="Email"
            Width: =Parent.Width - Self.X - 64
            X: =32
      - SendIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(255, 255, 255, 1)
            DisplayMode: =If(Len(Trim(TextEmailSubject.Text)) > 0 && !IsEmpty(MyPeople), DisplayMode.Edit, DisplayMode.Disabled)
            Icon: =Icon.Send
            OnSelect: |
              =Set(_emailRecipientString, Concat(MyPeople, Mail & ";"));
              Office365Outlook.SendEmail(_emailRecipientString, TextEmailSubject.Text, TextEmailMessage.Text, {Importance:"Normal"});
              Reset(TextEmailSubject);
              Reset(TextEmailMessage);
              Clear(MyPeople)
            Tooltip: ="Send message"
            X: =Parent.Width - Self.Width
      - RecipientLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Text: ="*To (" & CountRows(MyPeople) & ")"
            X: =32
            Y: =QuickActionBar.Height + 15
      - SearchBox:
          Control: Classic/TextInput@2.3.2
          Properties:
            AccessibleLabel: ="Search people or add email address. At least one recipient is required for a successful submission."
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            HintText: ="Search people or add email address"
            PaddingLeft: =50
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =RecipientLabel.Y + RecipientLabel.Height + 3
      - SearchIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            Icon: =Icon.Search
            X: =SearchBox.X + 5
            Y: =SearchBox.Y
      - AddIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            Icon: =Icon.Add
            OnSelect: |
              =Collect(MyPeople, {
                DisplayName: SearchBox.Text, 
                UserPrincipalName: SearchBox.Text, 
                Mail: SearchBox.Text
              });
              Reset(SearchBox)
            Visible: |
              =!IsBlank(SearchBox.Text) &&
              IsMatch(SearchBox.Text, Match.Email) &&
              Not(Trim(SearchBox.Text) in MyPeople.UserPrincipalName)
            X: =SearchBox.X + SearchBox.Width - Self.Width - 10
            Y: =SearchBox.Y
      - SelectedPeopleGallery:
          Control: Gallery@2.15.0
          Variant: SelectedUsersTabletGallery
          Properties:
            BorderColor: =SearchBox.BorderColor
            Height: =Min((Self.TemplateHeight + Self.TemplatePadding * 2) * RoundUp(CountRows(Self.AllItems) / 4, 0), 182)
            Items: =MyPeople
            TemplateSize: =42
            WrapCount: =4
            X: =27
            Y: =SearchBox.Y + SearchBox.Height
          Children:
            - PersonCard:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(56, 96, 178, 1)
                  Height: =Parent.TemplateHeight
                  Width: =Parent.TemplateWidth
            - PersonName:
                Control: Label@2.5.1
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Font: =Font.'Open Sans'
                  Height: =Parent.TemplateHeight
                  PaddingLeft: =10
                  Text: =ThisItem.DisplayName
                  Width: =Parent.TemplateWidth - RemoveIcon.Width + 10
            - RemoveIcon:
                Control: Classic/Icon@2.5.0
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Icon: =Icon.Cancel
                  OnSelect: =Remove(MyPeople, LookUp(MyPeople, UserPrincipalName = ThisItem.UserPrincipalName))
                  Tooltip: ="Select to remove user from collection"
                  X: =Parent.TemplateWidth - Self.Width
      - SubjectLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Text: ="*Subject"
            X: =32
            Y: =SelectedPeopleGallery.Y + SelectedPeopleGallery.Height + 16
      - SubjectInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            AccessibleLabel: ="A subject is required to send an email."
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            HintText: ="Add a subject"
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =SubjectLabel.Y + SubjectLabel.Height + 3
      - MessageLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Text: ="Message"
            X: =32
            Y: =SubjectInput.Y + SubjectInput.Height + 16
      - MessageInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            AccessibleLabel: ="Add a message"
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            Height: =238
            HintText: ="Add a message"
            Mode: =TextMode.MultiLine
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =MessageLabel.Y + MessageLabel.Height + 3
      - PeopleSearchGallery:
          Control: Gallery@2.15.0
          Variant: PeoplePickerGallerySmallTablet
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            BorderThickness: =2
            Height: =If(Self.Visible, Parent.Height / 2 + 200, 0)
            Items: =If(!IsBlank(Trim(SearchBox.Text)), Office365Users.SearchUser({searchTerm: Trim(SearchBox.Text), top: 15}))
            Visible: =!IsBlank(Trim(SearchBox.Text))
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =SearchBox.Y + SearchBox.Height
          Children:
            - PersonContainer:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  BorderThickness: =If(ThisItem.UserPrincipalName in MyPeople.UserPrincipalName, 4, 0)
                  Fill: =RGBA(0,0,0,0)
                  Height: =Parent.TemplateHeight
                  Width: =Parent.TemplateWidth
            - PersonDisplayName:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  OnSelect: |
                    =Set(_selectedUser, ThisItem);
                    Reset(SearchBox);
                    If(Not(ThisItem.UserPrincipalName in MyPeople.UserPrincipalName), Collect(MyPeople, ThisItem))
                  Size: =17
                  Text: =ThisItem.DisplayName
                  X: =16
                  Y: =4
            - PersonEmail:
                Control: Label@2.5.1
                Properties:
                  Color: =ColorFade(PersonDisplayName.Color, 0.20)
                  Font: =Font.'Open Sans'
                  Size: =17
                  Text: =ThisItem.UserPrincipalName
                  X: =PersonDisplayName.X
                  Y: =PersonDisplayName.Y + PersonDisplayName.Height + 3
```

### Key Components

#### People Picker Functionality
- **Search Integration**: Uses Office365Users.SearchUser for real-time people search
- **Email Validation**: IsMatch(Text, Match.Email) for email format validation
- **Collection Management**: MyPeople collection stores selected recipients
- **Duplicate Prevention**: Checks if user already exists before adding

#### Dynamic UI Elements
- **Recipient Counter**: Shows count of selected people in label
- **Add Button Visibility**: Only shows when valid email is entered
- **Send Button State**: Disabled until subject and recipients are provided
- **Search Results**: Overlay gallery that appears during search

#### Email Composition
- **Subject Field**: Required field with validation
- **Message Field**: Multi-line text input with 238px height
- **Send Functionality**: Integrates with Office365Outlook.SendEmail
- **Form Reset**: Clears fields after successful send

### Office 365 Integration

#### Required Connections
- **Office 365 Users**: For people search functionality
- **Office 365 Outlook**: For sending emails

#### API Calls
```powerapps
// Search for users
Office365Users.SearchUser({searchTerm: Trim(SearchBox.Text), top: 15})

// Send email
Office365Outlook.SendEmail(
  _emailRecipientString, 
  SubjectInput.Text, 
  MessageInput.Text, 
  {Importance:"Normal"}
)
```

### Data Management

#### Collections Used
- **MyPeople**: Stores selected email recipients
  - DisplayName: User's display name
  - UserPrincipalName: User's email/login
  - Mail: Email address for sending

#### Variables Used
- **_emailRecipientString**: Semicolon-separated recipient list
- **_selectedUser**: Currently selected user from search

### Validation Logic

#### Send Button Enablement
```powerapps
DisplayMode: =If(
  Len(Trim(SubjectInput.Text)) > 0 && !IsEmpty(MyPeople), 
  DisplayMode.Edit, 
  DisplayMode.Disabled
)
```

#### Email Format Validation
```powerapps
Visible: =!IsBlank(SearchBox.Text) &&
  IsMatch(SearchBox.Text, Match.Email) &&
  Not(Trim(SearchBox.Text) in MyPeople.UserPrincipalName)
```

### Use Cases
- Internal company communications
- Team notifications and updates
- Project collaboration emails
- Meeting invitations and follow-ups
- Document sharing notifications
- Workflow approval notifications

### Customization Options
- **Branding**: Modify colors and fonts to match company theme
- **Field Requirements**: Add/remove required fields
- **Email Templates**: Pre-populate subject/message for specific scenarios
- **Recipient Limits**: Add validation for maximum recipients
- **Attachment Support**: Extend with file attachment capabilities
- **Priority Settings**: Add importance/priority selection options#
# People Template

### Overview
A dedicated people picker and directory screen with Office 365 integration, profile photos, search functionality, and selected users management. Features empty state handling and real-time search results.

### Key Features
- Office 365 Users integration with profile photos
- Real-time people search with Office365Users.SearchUser
- Selected users collection management (MyPeople)
- Profile photo integration with Office365Users.UserPhotoV2
- Empty state with helpful messaging
- Responsive gallery layouts for different screen sizes

### Structure
```yaml
Screens:
  PeopleScreen:
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
            Color: =RGBA(255, 255, 255, 1)
            Font: =Font.'Open Sans'
            Height: =64
            Size: =18
            Text: ="People"
            Width: =Parent.Width - Self.X * 2
            X: =32
      - SearchBox:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            BorderStyle: =BorderStyle.None
            Font: =Font.'Open Sans'
            HintText: ="Search"
            PaddingLeft: =70
            RadiusBottomLeft: =0
            RadiusBottomRight: =0
            RadiusTopLeft: =0
            RadiusTopRight: =0
            Width: =Parent.Width
            Y: =QuickActionBar.Height
      - SearchIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            Icon: =Icon.Search
            Height: =SearchBox.Height
            Width: =SearchBox.Height
            X: =24
            Y: =SearchBox.Y
      - SearchSeparator:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(0, 18, 107, 1)
            Height: =1
            Width: =Parent.Width
            Y: =SearchBox.Y + SearchBox.Height
      - SelectedPeopleGallery:
          Control: Gallery@2.15.0
          Variant: SelectedUsersTabletGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Items: =MyPeople
            WrapCount: =4
            X: =0
            Y: =SearchBox.Y + SearchBox.Height + 8
          Children:
            - PersonCard:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(56, 96, 178, 1)
                  Height: =Parent.TemplateHeight
                  Width: =Parent.TemplateWidth
            - PersonName:
                Control: Label@2.5.1
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Font: =Font.'Open Sans'
                  Height: =Parent.TemplateHeight
                  OnSelect: =Set(_selectedUser, ThisItem)
                  PaddingLeft: =10
                  Text: =ThisItem.DisplayName
                  Width: =Parent.TemplateWidth - RemoveIcon.Width + 10
            - RemoveIcon:
                Control: Classic/Icon@2.5.0
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Icon: =Icon.Cancel
                  OnSelect: =Remove(MyPeople, LookUp(MyPeople, UserPrincipalName = ThisItem.UserPrincipalName))
                  Tooltip: ="Select to remove user from collection"
                  X: =Parent.TemplateWidth - Self.Width
      - EmptyStateIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            DisplayMode: =DisplayMode.View
            Height: =55
            Icon: =Icon.Person
            Visible: =IsEmpty(MyPeople)
            Width: =55
            X: =Parent.Width / 2 - Self.Width/2
            Y: =Parent.Height / 2 - Self.Height / 2 - 100
      - EmptyStateLabel:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            Font: =Font.'Open Sans'
            Height: =50
            Size: =19
            Text: ="Find users in your organization"
            Visible: =IsEmpty(MyPeople)
            Width: =535
            X: =Parent.Width / 2 - Self.Width/2
            Y: =EmptyStateIcon.Y + EmptyStateIcon.Height + 20
      - SearchResultsGallery:
          Control: Gallery@2.15.0
          Variant: PeoplePickerTabletGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Items: =If(!IsBlank(Trim(SearchBox.Text)), Office365Users.SearchUser({searchTerm: Trim(SearchBox.Text), top: 15}))
            TemplateSize: =87
            Visible: =!IsBlank(Trim(SearchBox.Text))
            Width: =Parent.Width
            X: =0
            Y: =SearchBox.Y + SearchBox.Height
          Children:
            - SelectionBorder:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  BorderThickness: =If(ThisItem.UserPrincipalName in MyPeople.UserPrincipalName, 2, 0)
                  Fill: =RGBA(0,0,0,0)
                  Height: =Parent.TemplateHeight - 2*Self.Y
                  Width: =Parent.TemplateWidth - 2*Self.X
                  X: =1
                  Y: =1
            - DefaultUserIcon:
                Control: Classic/Icon@2.5.0
                Properties:
                  Color: =RGBA(255, 255, 255, 1)
                  Fill: =RGBA(56, 96, 178, 1)
                  Height: =ProfilePhoto.Height
                  Icon: =Icon.Person
                  OnSelect: =Select(UserName)
                  Width: =ProfilePhoto.Width
                  X: =ProfilePhoto.X
                  Y: =ProfilePhoto.Y
            - ProfilePhoto:
                Control: Image@2.2.3
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Height: =Self.Width
                  Image: =If(!IsBlank(ThisItem.Id), Office365Users.UserPhotoV2(ThisItem.Id))
                  OnSelect: =Select(UserName)
                  Width: =Parent.TemplateHeight - 30
                  X: =37
                  Y: =(Parent.TemplateHeight / 2) - (Self.Height/2)
            - UserName:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Semibold
                  Height: =Self.Size * 1.8
                  OnSelect: |
                    =Set(_selectedUser, ThisItem);
                    Reset(SearchBox);
                    If(Not(ThisItem.UserPrincipalName in MyPeople.UserPrincipalName), Collect(MyPeople, ThisItem))
                  Size: =12
                  Text: =ThisItem.DisplayName
                  Width: =Parent.TemplateWidth - 232
                  X: =ProfilePhoto.X + ProfilePhoto.Width + 16
                  Y: =16
            - UserEmail:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  Height: =Self.Size * 1.8
                  OnSelect: =Select(UserName)
                  Size: =12
                  Text: =ThisItem.UserPrincipalName
                  Width: =UserName.Width
                  X: =UserName.X
                  Y: =Parent.TemplateHeight - Self.Height - 20
            - ItemSeparator:
                Control: Rectangle@2.3.0
                Properties:
                  BorderColor: =RGBA(0, 18, 107, 1)
                  Fill: =RGBA(0, 18, 107, 1)
                  Height: =1
                  Width: =Parent.TemplateWidth
                  Y: =Parent.TemplateHeight - 1
```

### Key Components

#### Search Functionality
- **Real-time Search**: Uses Office365Users.SearchUser for instant results
- **Search Input**: Full-width search box with integrated search icon
- **Results Overlay**: Search results appear over selected people when typing
- **Auto-clear**: Search box clears when user is selected

#### Profile Integration
- **Profile Photos**: Uses Office365Users.UserPhotoV2 for user photos
- **Fallback Icon**: Shows person icon when photo unavailable
- **User Information**: Displays DisplayName and UserPrincipalName
- **Visual Selection**: Border highlight for already selected users

#### Collection Management
- **MyPeople Collection**: Stores selected users with full user objects
- **Duplicate Prevention**: Checks existing collection before adding
- **Remove Functionality**: X button to remove users from selection
- **Selection State**: Visual indicators for selected users

#### Empty State
- **Helpful Messaging**: "Find users in your organization" guidance
- **Visual Icon**: Person icon for empty state
- **Conditional Display**: Only shows when MyPeople collection is empty

### Office 365 Integration

#### Required Connections
- **Office 365 Users**: For user search and profile data

#### API Calls
```powerapps
// Search for users
Office365Users.SearchUser({searchTerm: Trim(SearchBox.Text), top: 15})

// Get user profile photo
Office365Users.UserPhotoV2(ThisItem.Id)
```

### Data Management

#### Collections Used
- **MyPeople**: Selected users collection
  - DisplayName: User's display name
  - UserPrincipalName: User's email/login
  - Id: User's unique identifier
  - (All other Office 365 user properties)

#### Variables Used
- **_selectedUser**: Currently selected user from search results

### Gallery Variants

#### SelectedUsersTabletGallery
- **Purpose**: Display selected users in card format
- **Layout**: 4 columns (WrapCount=4)
- **Features**: Remove functionality, compact display

#### PeoplePickerTabletGallery
- **Purpose**: Display search results with profiles
- **Layout**: Vertical list with photos and details
- **Features**: Profile photos, selection state, detailed info

### Visual Design

#### Color Scheme
- **Primary Blue**: RGBA(56, 96, 178, 1) for headers and selected items
- **Dark Blue**: RGBA(0, 18, 107, 1) for borders and accents
- **White Text**: High contrast on blue backgrounds
- **Transparent Overlays**: For selection states and interactions

#### Layout Structure
1. **Fixed Header**: Blue header with app title
2. **Search Bar**: Full-width search with icon
3. **Selected People**: Grid of selected users (when not searching)
4. **Search Results**: List of search results (when searching)
5. **Empty State**: Helpful message when no users selected

### Use Cases
- **Team Building**: Select team members for projects
- **Meeting Invitations**: Choose attendees for meetings
- **Permission Management**: Select users for access control
- **Contact Lists**: Build custom contact groups
- **Collaboration**: Choose collaborators for documents
- **Notification Lists**: Select users for announcements

### Responsive Behavior
- **Search Overlay**: Search results overlay selected users during search
- **Grid Layout**: Selected users display in responsive 4-column grid
- **Full-width Elements**: Search and results span full screen width
- **Touch-friendly**: Large touch targets for mobile interaction

### Customization Options
- **Search Limit**: Modify 'top: 15' parameter for more/fewer results
- **Grid Columns**: Change WrapCount for different column layouts
- **Profile Size**: Adjust profile photo dimensions
- **Empty State**: Customize messaging and icons
- **Selection Limits**: Add validation for maximum selections
- **Additional Fields**: Display more user properties (department, title, etc.)#

## Responsive Header Utility (Back + Title/Subtitle + Badge)

Reusable header block that adapts across breakpoints and guarantees mobile visibility.

```yaml
- UtilityResponsiveHeader:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
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
          Screen.Size = 1,
          Back.Height + TitleBlock.Height + Badge.Height + (Self.LayoutGap * 2) + Self.PaddingTop + Self.PaddingBottom,
          Max(Back.Height, TitleBlock.Height, Badge.Height) + Self.PaddingTop + Self.PaddingBottom
        )
    Children:
      - Back:
          Control: Button@0.0.45
          Properties:
            Height: =32
            Icon: ="ArrowLeft"
            Layout: ='ButtonCanvas.Layout'.IconBeforeText
            Text: ="Back"
      - TitleBlock:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            FillPortions: =1
            LayoutDirection: =LayoutDirection.Vertical
            LayoutAlignItems: =LayoutAlignItems.Stretch
            LayoutWrap: =false
            LayoutGap: =2
          Children:
            - Title: { Control: Label@2.5.1, Properties: { AutoHeight: =true, FontWeight: =FontWeight.Bold, Size: =15, Text: ="[Title]" } }
            - Subtitle: { Control: Label@2.5.1, Properties: { AutoHeight: =true, Text: ="[Subtitle]" } }
      - Badge:
          Control: Label@2.5.1
          Properties:
            Color: =RGBA(255, 0, 0, 1)
            DisplayMode: =DisplayMode.View
            Size: =10
            Text: ="[Status]"
```
# Meeting Template

### Overview
A comprehensive meeting scheduler with Office 365 integration featuring attendee management, intelligent time finding, room booking, and calendar integration. Uses advanced Office 365 APIs for finding optimal meeting times and available rooms.

### Key Features
- Dual-tab interface (Invite/Schedule) for organized workflow
- Office 365 integration with FindMeetingTimes and room booking
- Intelligent meeting time suggestions based on attendee availability
- Room list and room availability checking
- People picker with search functionality
- Calendar integration with Office365Outlook.V2CalendarPostItem

### Structure
```yaml
Screens:
  MeetingScreen:
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
            Color: =RGBA(255, 255, 255, 1)
            Font: =Font.'Open Sans'
            Height: =64
            Size: =18
            Text: ="Meeting"
            Width: =356
            X: =20
      - SendIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(255, 255, 255, 1)
            DisplayMode: =If(Len(Trim(SubjectInput.Text)) > 0 && !IsEmpty(MyPeople) && !IsBlank(_selectedMeetingTime), DisplayMode.Edit, DisplayMode.Disabled)
            Icon: =Icon.Send
            OnSelect: |
              =Set(_myCalendarName, LookUp(Office365Outlook.CalendarGetTables().value, DisplayName = "Calendar").Name);
              Set(_myScheduledMeeting, Office365Outlook.V2CalendarPostItem(
                _myCalendarName,
                SubjectInput.Text, 
                Text(DateAdd(DateTimeValue(_selectedMeetingTime.StartTime), -TimeZoneOffset(), TimeUnit.Minutes)),
                Text(DateAdd(DateTimeValue(_selectedMeetingTime.EndTime), -TimeZoneOffset(), TimeUnit.Minutes)),
                {
                  RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";") & _selectedRoom.Address, 
                  Body: MessageInput.Text, 
                  Location: _selectedRoom.Name, 
                  Importance: "Normal", 
                  ShowAs: "Busy", 
                  ResponseRequested: true
                }
              ));
              Reset(SubjectInput);
              Reset(MessageInput);
              Clear(MyPeople);
              Set(_selectedMeetingTime, Blank());
              Set(_selectedRoom, Blank())
            Tooltip: ="Send invite"
            X: =Parent.Width - Self.Width
      - InviteTab:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            Color: =If(_showDetails, RGBA(96, 94, 92, 1), RGBA(56, 96, 178, 1))
            Font: =Font.'Open Sans'
            FontWeight: =If(_showDetails, FontWeight.Normal, FontWeight.Semibold)
            Height: =25
            OnSelect: =Set(_showDetails, false)
            Size: =12
            Text: ="Invite"
            Width: =Parent.Width / 2 - 55.5
            X: =32
            Y: =QuickActionBar.Height + 16
      - ScheduleTab:
          Control: Label@2.5.1
          Properties:
            Align: =Align.Center
            Color: =If(!_showDetails, RGBA(96, 94, 92, 1), RGBA(56, 96, 178, 1))
            Font: =Font.'Open Sans'
            FontWeight: =If(!_showDetails, FontWeight.Normal, FontWeight.Semibold)
            Height: =25
            OnSelect: =Set(_showDetails, true)
            Size: =12
            Text: ="Schedule"
            Width: =Parent.Width / 2 - 55.5
            X: =InviteTab.X + InviteTab.Width + 3
            Y: =QuickActionBar.Height + 16
      - TabIndicator:
          Control: Rectangle@2.3.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Fill: =RGBA(56, 96, 178, 1)
            Height: =2
            Width: =InviteTab.Width + 3
            X: =If(_showDetails, ScheduleTab.X - 1.5, InviteTab.X - 1.5)
            Y: =InviteTab.Y + InviteTab.Height + 8
      
      # Invite Tab Content
      - AttendeesLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =26
            Text: ="*Attendees (" & CountRows(MyPeople) & ")"
            Visible: =!_showDetails
            Width: =200
            X: =32
            Y: =TabIndicator.Y + TabIndicator.Height + 24
      - AttendeeSearch:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            HintText: ="Search for people"
            PaddingLeft: =40
            Visible: =!_showDetails
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =AttendeesLabel.Y + AttendeesLabel.Height + 6
      - AttendeeSearchIcon:
          Control: Classic/Icon@2.5.0
          Properties:
            Color: =RGBA(0, 18, 107, 1)
            Icon: =Icon.Search
            Visible: =!_showDetails
            X: =AttendeeSearch.X
            Y: =AttendeeSearch.Y
      - SelectedAttendeesGallery:
          Control: Gallery@2.15.0
          Variant: SelectedUsersGalleryMeetingVariant
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Min(58 * RoundUp(CountRows(Self.AllItems) / 4, 0), 114)
            Items: =MyPeople
            TemplateSize: =42
            Visible: =!_showDetails
            WrapCount: =4
            X: =32
            Y: =AttendeeSearch.Y + AttendeeSearch.Height
      - SubjectLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =25
            Text: ="*Subject"
            Visible: =!_showDetails
            X: =32
      - SubjectInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            HintText: ="Add a subject"
            Visible: =!_showDetails
            Width: =Parent.Width - Self.X * 2
            X: =32
      - MessageLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =25
            Text: ="Message"
            Visible: =!_showDetails
            X: =32
      - MessageInput:
          Control: Classic/TextInput@2.3.2
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Font: =Font.'Open Sans'
            Height: =238
            HintText: ="Add a message"
            Mode: =TextMode.MultiLine
            Visible: =!_showDetails
            Width: =Parent.Width - Self.X * 2
            X: =32

      # Schedule Tab Content
      - DateLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =25
            Text: ="*Date"
            Visible: =_showDetails
            Width: =Parent.Width / 2 - 55.5
            X: =32
      - DatePicker:
          Control: Classic/DatePicker@2.6.0
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            DisplayMode: =If(IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit)
            Font: =Font.'Open Sans'
            IconBackground: =RGBA(56, 96, 178, 1)
            IconFill: =RGBA(255, 255, 255, 1)
            OnSelect: |
              =ClearCollect(MeetingTimes, AddColumns(
                Office365Outlook.FindMeetingTimes({
                  RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";"), 
                  MeetingDuration: DurationDropdown.Selected.Minutes,
                  Start: Text(DateAdd(DatePicker.SelectedDate, 8, TimeUnit.Hours), DateTimeFormat.UTC), 
                  End: Text(DateAdd(DatePicker.SelectedDate, 17, TimeUnit.Hours), DateTimeFormat.UTC),
                  MaxCandidates: 15, 
                  MinimumAttendeePercentage: 1, 
                  IsOrganizerOptional: false, 
                  ActivityDomain: "Work"
                }).MeetingTimeSuggestions,
                StartTime, MeetingTimeSlot.Start.DateTime, 
                EndTime, MeetingTimeSlot.End.DateTime
              ));
              Set(_showMeetingTimes, true)
            Visible: =_showDetails
            Width: =Parent.Width / 2 - 55.5
            X: =32
      - DurationLabel:
          Control: Label@2.5.1
          Properties:
            Font: =Font.'Open Sans'
            Height: =25
            Text: ="*Duration"
            Visible: =_showDetails
            Width: =Parent.Width / 2 - 55.5
            X: =DateLabel.X + DateLabel.Width + 18.5
      - DurationDropdown:
          Control: Classic/DropDown@2.3.1
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            ChevronBackground: =RGBA(56, 96, 178, 1)
            ChevronFill: =RGBA(255, 255, 255, 1)
            DisplayMode: =If(IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit)
            Font: =Font.'Open Sans'
            Items: =Table(
              {Name: "0.5 hour(s)", Minutes: 30},
              {Name: "1 hour(s)", Minutes: 60},
              {Name: "1.5 hour(s)", Minutes: 90},
              {Name: "2 hour(s)", Minutes: 120},
              {Name: "2.5 hour(s)", Minutes: 150},
              {Name: "3 hour(s)", Minutes: 180},
              {Name: "3.5 hour(s)", Minutes: 210},
              {Name: "4 hour(s)", Minutes: 240}
            )
            Visible: =_showDetails
            Width: =Parent.Width / 2 - 55.5
            X: =DurationLabel.X
      - MeetingTimesGallery:
          Control: Gallery@2.15.0
          Variant: MeetingTimesGallery
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =205
            Items: =MeetingTimes
            TemplateSize: =71
            Visible: =_showMeetingTimes && _showDetails && !IsEmpty(MyPeople)
            Width: =Parent.Width
          Children:
            - TimeSlot:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Semibold
                  Height: =35
                  OnSelect: |
                    =Set(_selectedMeetingTime, ThisItem);
                    ClearCollect(AvailableRooms, Office365Outlook.GetRooms().value);
                    Set(_showRooms, true)
                  Text: =Text(DateAdd(DateTimeValue(ThisItem.StartTime), -TimeZoneOffset(), TimeUnit.Minutes), DateTimeFormat.ShortTime)
                  Width: =160
                  X: =37
                  Y: =5
            - AvailabilityInfo:
                Control: Label@2.5.1
                Properties:
                  Color: =ColorFade(RGBA(50, 49, 48, 1), 0.20)
                  Font: =Font.'Open Sans'
                  Text: =If(ThisItem.Confidence = 100, "All attendees available", "Some conflicts")
                  X: =37
                  Y: =TimeSlot.Y + TimeSlot.Height + 2
      - RoomsGallery:
          Control: Gallery@2.15.0
          Variant: RoomsListVariant
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =Parent.Height - Self.Y
            Items: =AvailableRooms
            TemplateSize: =71
            Visible: =_showDetails && !IsBlank(_selectedMeetingTime) && _showRooms
            Width: =Parent.Width
          Children:
            - RoomName:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Semibold
                  OnSelect: =Set(_selectedRoom, ThisItem)
                  Text: =ThisItem.Name
                  X: =37
                  Y: =Parent.TemplateHeight / 2 - Self.Height / 2
      - PeopleSearchGallery:
          Control: Gallery@2.15.0
          Variant: PeoplePickerGallerySmallMeetingVariant
          Properties:
            BorderColor: =RGBA(0, 18, 107, 1)
            Height: =If(Len(Trim(AttendeeSearch.Text)) > 0, Parent.Height - Self.Y - 10, 0)
            Items: =If(!IsBlank(Trim(AttendeeSearch.Text)), Office365Users.SearchUser({searchTerm: Trim(AttendeeSearch.Text), top: 15}))
            Visible: =!_showDetails && Len(Trim(AttendeeSearch.Text)) > 0
            Width: =Parent.Width - Self.X * 2
            X: =32
            Y: =AttendeeSearch.Y + AttendeeSearch.Height
          Children:
            - PersonName:
                Control: Label@2.5.1
                Properties:
                  Font: =Font.'Open Sans'
                  FontWeight: =FontWeight.Semibold
                  OnSelect: |
                    =Reset(AttendeeSearch);
                    Set(_selectedUser, ThisItem);
                    If(Not(ThisItem.UserPrincipalName in MyPeople.UserPrincipalName), Collect(MyPeople, ThisItem))
                  Text: =ThisItem.DisplayName
                  X: =16
            - PersonEmail:
                Control: Label@2.5.1
                Properties:
                  Color: =ColorFade(PersonName.Color, 0.20)
                  Font: =Font.'Open Sans'
                  Text: =ThisItem.UserPrincipalName
                  X: =PersonName.X
                  Y: =PersonName.Y + PersonName.Height + 3
```

### Key Components

#### Tab Interface
- **Dual Tabs**: Invite tab for attendees/content, Schedule tab for timing/location
- **Tab Indicator**: Animated blue bar that moves between tabs
- **State Management**: _showDetails variable controls tab visibility

#### Office 365 Integration

##### Meeting Time Finding
```powerapps
Office365Outlook.FindMeetingTimes({
  RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";"), 
  MeetingDuration: DurationDropdown.Selected.Minutes,
  Start: Text(DateAdd(DatePicker.SelectedDate, 8, TimeUnit.Hours), DateTimeFormat.UTC), 
  End: Text(DateAdd(DatePicker.SelectedDate, 17, TimeUnit.Hours), DateTimeFormat.UTC),
  MaxCandidates: 15, 
  MinimumAttendeePercentage: 1, 
  IsOrganizerOptional: false, 
  ActivityDomain: "Work"
})
```

##### Calendar Integration
```powerapps
Office365Outlook.V2CalendarPostItem(
  _myCalendarName,
  SubjectInput.Text, 
  StartTime,
  EndTime,
  {
    RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";") & _selectedRoom.Address, 
    Body: MessageInput.Text, 
    Location: _selectedRoom.Name, 
    Importance: "Normal", 
    ShowAs: "Busy", 
    ResponseRequested: true
  }
)
```

##### Room Management
```powerapps
// Get room lists
Office365Outlook.GetRoomLists().value

// Get rooms in a room list
Office365Outlook.GetRoomsInRoomList(RoomListAddress).value

// Get all rooms
Office365Outlook.GetRooms().value
```

#### Data Collections

##### MyPeople Collection
- Stores selected meeting attendees
- Used for FindMeetingTimes API calls
- Displays in selected users gallery

##### MeetingTimes Collection
- Stores available meeting time suggestions
- Includes StartTime, EndTime, Confidence, AttendeeAvailability
- Populated by FindMeetingTimes API

##### Room Collections
- **RoomsLists**: Available room lists in tenant
- **AllRooms**: Rooms within selected room list
- **AvailableRooms**: Rooms available at selected time
- **RoomTimeSuggestions**: Room availability data

#### State Variables

##### UI State
- **_showDetails**: Controls Invite/Schedule tab visibility
- **_showMeetingTimes**: Shows/hides meeting time suggestions
- **_showRooms**: Controls room list visibility
- **_roomListSelected**: Tracks if user is viewing rooms in a list

##### Selection State
- **_selectedMeetingTime**: Currently selected meeting time
- **_selectedRoom**: Currently selected room
- **_selectedRoomList**: Currently selected room list
- **_selectedUser**: Currently selected user from search

##### Loading State
- **_loadingMeetingTimes**: Shows loading state for time search
- **_loadingRooms**: Shows loading state for room search

### Advanced Features

#### Intelligent Time Finding
- **Attendee Availability**: Checks all attendees' calendars
- **Confidence Scoring**: Shows percentage of attendees available
- **Conflict Resolution**: Displays who has conflicts for each time slot
- **Business Hours**: Searches within 8 AM - 5 PM range
- **Duration Flexibility**: Supports 30 minutes to 4 hours

#### Room Booking Integration
- **Room Lists**: Supports organizational room list structure
- **Room Availability**: Checks room calendars for conflicts
- **Fallback Logic**: Handles tenants without room lists
- **Search Functionality**: Filter rooms by name or location
- **Automatic Selection**: Includes room in meeting invite

#### Validation Logic
- **Send Button**: Disabled until subject, attendees, and time selected
- **Date Picker**: Disabled until attendees selected
- **Duration Dropdown**: Disabled until attendees selected
- **Email Validation**: Validates manually entered email addresses

### Use Cases
- **Team Meetings**: Schedule recurring team meetings with room booking
- **Client Meetings**: Find optimal times across organizations
- **All-Hands**: Large meetings with multiple attendees
- **Training Sessions**: Book training rooms with equipment
- **Project Kickoffs**: Coordinate stakeholder availability
- **Board Meetings**: Executive scheduling with room requirements

### Customization Options
- **Time Ranges**: Modify business hours (8 AM - 5 PM default)
- **Duration Options**: Add/remove meeting duration choices
- **Room Filtering**: Add room capacity or equipment filters
- **Attendee Limits**: Set maximum number of attendees
- **Timezone Handling**: Customize timezone offset calculations
- **Meeting Types**: Add meeting type selection (in-person, virtual, hybrid)
- **Recurrence**: Extend with recurring meeting options

### Performance Considerations
- **API Limits**: FindMeetingTimes limited to 15 candidates
- **Room Limits**: Room queries limited to first 20 rooms
- **Concurrent Operations**: Uses Concurrent() for parallel API calls
- **Collection Management**: Efficient collection updates and clearing
- **Loading States**: Proper loading indicators for API calls