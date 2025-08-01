# Power Apps Component Structure

## Key Component Types

### Layout Components

- **GroupContainer@1.3.0**: Main layout container
  - Variant: AutoLayout
  - Properties: LayoutDirection, LayoutGap, LayoutAlignItems, FillPortions

### Interactive Components

- **Classic/Button@2.2.0**: Standard buttons
- **Classic/Icon@2.5.0**: Icon buttons with OnSelect actions
- **Classic/TextInput@2.3.2**: Input fields
- **Classic/ComboBox@2.4.0**: Dropdown selections
- **Classic/DatePicker@2.6.0**: Date selection

### Display Components

- **Label@2.5.1**: Text display elements
- **Rectangle@2.3.0**: Shape/separator elements
- **Gallery@2.15.0**: List/grid displays

### Form Components

- **Form@2.4.4**: Data forms with DataCards
- **TypedDataCard@1.0.7**: Form field containers

## Control Hierarchy Pattern

```
Screen
└── GroupContainer (ScreenContainer)
    ├── GroupContainer (Header/TableNameContainer)
    └── GroupContainer (Body)
        ├── GroupContainer (Sidebar)
        │   ├── GroupContainer (SearchContainer)
        │   ├── GroupContainer (NewRecordButtonBar)
        │   └── Gallery (RecordsList)
        └── GroupContainer (RightContainer/MainContent)
            ├── GroupContainer (SelectedRecordHeader)
            └── GroupContainer (MainContainer)
                └── Form (with DataCards)
```
