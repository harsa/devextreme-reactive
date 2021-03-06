# TableGroupRow Plugin Reference

A plugin that renders group rows. Enables expanding and collapsing them.

## User Reference

### Dependencies

- [GroupingState](grouping-state.md)
- [TableView](table-view.md)
- [DataTypeProvider](data-type-provider.md) [Optional]

### Properties

Name | Type | Default | Description
-----|------|---------|------------
groupCellTemplate | (args: [GroupCellArgs](#group-cell-args)) => ReactElement | | A component that renders a group row
groupIndentCellTemplate | (args: [GroupIndentCellArgs](#group-indent-cell-args)) => ReactElement | null | A component that renders a group indent cell
groupRowTemplate | (args: [GroupRowArgs](#group-row-args)) => ReactElement | | A component that renders a group row
groupIndentColumnWidth | number | | The group indent column's width
showColumnWhenGrouped | (args: columnName) => boolean | null | A custom function that returns a boolean value defining if the grid displays the column by which data is grouped.

## Interfaces

### <a name="column"></a>Column (Extension)

A value with the [Column](grid.md#column) shape extended by the following fields:

Field | Type | Description
------|------|------------
showWhenGrouped? | boolean | Specifies if the grid displays the column by which data is grouped.
title? | string | Specifies a table column title.

### <a name="group-cell-args"></a>GroupCellArgs

Describes the properties passed to the template that renders a group row.

A value with the [TableCellArgs](table-view.md#table-cell-args) shape extended by the following fields:

Field | Type | Description
------|------|------------
row | [GroupRow](#group-row) | The group row's data object
column | [Column](#column) | The column associated with the group
isExpanded | boolean | Specifies if the row is expanded
toggleGroupExpanded | () => void | Toggles the group row's expanded state

### <a name="group-row-args"></a>GroupRowArgs

Describes the properties passed to the template that renders a group row.

A value with the [TableRowArgs](table-view.md#table-row-args) shape extended by the following fields:

Field | Type | Description
------|------|------------
row | [GroupRow](#group-row) | The group row's data object

### <a name="group-indent-cell-args"></a>GroupIndentCellArgs

Describes properties passed to the template that renders a group indent cell.

A value with the [TableCellArgs](table-view.md#table-cell-args) shape extended by the following fields:

Field | Type | Description
------|------|------------
row | [GroupRow](#group-row) | The group row's data object
column | [Column](#column) | The column associated with the group

### <a name="group-row"></a>GroupRow

Describes the group row data structure.

Field | Type | Description
------|------|------------
type | 'groupRow' | A string value that identifies the group row
value | any | The current group key value

## Plugin Developer Reference

### Imports

Name | Plugin | Type | Description
-----|--------|------|------------
tableColumns | Getter | Array&lt;[TableColumn](table-view.md#table-column)&gt; | Table columns
tableBodyRows | Getter | Array&lt;[TableRow](table-view.md#table-row)&gt; | Table body rows
grouping | Getter | Array&lt;[Grouping](grouping-state.md#grouping)&gt; | Columns used for grouping
draftGrouping | Getter | Array&lt;[DraftGrouping](grouping-state.md#draft-grouping)&gt; | Grouping options used for preview
expandedGroups | Getter | Set&lt;[GroupKey](grouping-state.md#group-key)&gt; | Expanded groups
toggleGroupExpanded | Action | ({ groupKey: [GroupKey](grouping-state.md#group-key) }) => void | Toggles the expanded group state
tableViewCell | Template | [TableCellArgs](table-view.md#table-cell-args) | A template that renders a table cell
tableViewRow | Template | [TableRowArgs](table-view.md#table-row-args) | A template that renders a table row

### Exports

Name | Plugin | Type | Description
-----|--------|------|------------
tableColumns | Getter | Array&lt;[TableColumn](table-view.md#table-column)&gt; | Table columns, including the ones by which the table is grouped
tableBodyRows | Getter | Array&lt;[TableRow](table-view.md#table-column)&gt; | Table body rows with modified group rows
