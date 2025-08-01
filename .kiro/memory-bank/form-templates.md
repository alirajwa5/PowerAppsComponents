# Form Templates

## Header and Form View Template

### Overview
A dedicated form layout with header and scrollable form container. Features a single-column form with comprehensive field types and action buttons.

### Key Features
- Scrollable form container with LayoutOverflowY=Scroll
- Single-column form with Width=1300 for wide fields
- Comprehensive field types (TextInput, DatePicker, ComboBox)
- Action button layout with Cancel/Submit pattern

### Structure
```yaml
- FormContainer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      FillPortions: =7
      LayoutDirection: =LayoutDirection.Vertical
      LayoutGap: =16
      LayoutOverflowY: =LayoutOverflow.Scroll
      PaddingBottom: =15
      PaddingLeft: =15
      PaddingRight: =15
      PaddingTop: =15
    Children:
      - DataForm:
          Control: Form@2.4.4
          Layout: Vertical
          Properties:
            DataSource: =Applicant
            DefaultMode: =FormMode.New
            NumberOfColumns: =1
        Children:
          - FieldDataCard:
              Control: TypedDataCard@1.0.7
              Variant: TextualEdit
              Properties:
                Width: =1300
                DataField: ="field_name"
      - ButtonContainer:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            LayoutDirection: =LayoutDirection.Horizontal
            LayoutGap: =10
            LayoutJustifyContent: =LayoutJustifyContent.End
          Children:
            - CancelButton:
                Control: Button@0.0.45
                Properties:
                  Appearance: ='ButtonCanvas.Appearance'.Secondary
                  Text: ="Cancel"
                  Width: =120
            - SubmitButton:
                Control: Button@0.0.45
                Properties:
                  Text: ="Submit"
                  Width: =120
```

### Use Cases
- Data entry forms, Edit forms, Registration forms, Settings pages, Survey forms

## Approval Request Form Template

### Overview
A comprehensive form layout for approval workflows with a main form area (70%) and reviewer sidebar (30%). Features a complete data entry form with various field types and an approval workflow tracker.

### Key Features
- Form-Sidebar layout with 7:2 ratio (70% form, 30% sidebar)
- Complete form with multiple field types
- Approval workflow with visual reviewer progress
- Responsive sidebar that hides on small screens

### Use Cases
- Approval workflows, Application forms, Review processes, Data entry, Workflow tracking

## Table and Form Template

### Overview
A comprehensive master-detail layout combining table list view with form editing capabilities. Features responsive design, CRUD operations, search functionality, and delete confirmation dialogs.

### Key Features
- Master-detail layout with table list (30%) + form detail (70%)
- Responsive design that adapts to mobile
- Complete CRUD operations with delete confirmation
- Search functionality and state management
- Two-column form with scrollable content

### State Variables
- newMode, editMode, deleteMode, isItemSelected, CurrentItem, selectedRecord

### Structure Highlights
```yaml
- SidebarContainer:
    Properties:
      FillPortions: =If(And(Screen.Size = ScreenSize.Small, Or(newMode, isItemSelected)), 0, 3)
      Visible: =If(And(Screen.Size = ScreenSize.Small, Or(newMode, isItemSelected)), false, true)
    Children:
      - SearchContainer:
          Control: GroupContainer@1.3.0
          Children:
            - SearchInput:
                Control: TextInput@0.0.54
                Properties:
                  Placeholder: ="Search"
      - DataTable:
          Control: Table@1.0.278
          Properties:
            EnableRangeSelection: ='PowerAppsOneGrid.EnableRangeSelection'.Enable
            EnableSorting: ='PowerAppsOneGrid.EnableSorting'.Enable
            ReflowBehavior: ='PowerAppsOneGrid.ReflowBehavior'.ListOnly

- RightContainer:
    Properties:
      FillPortions: =7
    Children:
      - ActionBarContainer:
          Children:
            - NewButton, EditButton, DeleteButton
      - FormContainer:
          Children:
            - DataForm:
                Properties:
                  NumberOfColumns: =2
                  DefaultMode: =If(newMode, FormMode.New, editMode, FormMode.Edit, FormMode.View)
```

### Use Cases
- Admin panels, CRM systems, Inventory management, HR systems, Project management