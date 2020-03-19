---
title: Checkbox Table
toc: true
date: 2020-03-09 19:04:47
tags:
	- Vue-good-table
categories:
	- Vue-good-table
---

# Checkbox Table

One of the most common customizations in datatables is selectable rows. Creating a checkbox table with **vue-good-table** is easier than ever.


## Configuration 

type: `Object`

Object containing select options
```html
<vue-good-table
  @on-selected-rows-change="selectionChanged"
  :columns="columns"
  :rows="rows"
  :selectOptions="{
    enabled: true,
    selectOnCheckboxOnly: true, // only select when checkbox is clicked instead of the row
    selectionInfoClass: 'custom-class',
    selectionText: 'rows selected',
    clearSelectionText: 'clear',
    disableSelectInfo: true, // disable the select info panel on top
  }">
```

Although, the `on-selected-rows-change` event should be enough for you to keep track of selected rows. If at any time you need to know what rows are selected, you can get it via ref.

```js
this.$refs['my-table'].selectedRows;
```

### Example
```vue
<vue-good-table
  @on-selected-rows-change="selectionChanged"
  :columns="columns"
  :rows="rows"
  :select-options="{ enabled: true }"
  :search-options="{ enabled: true }">
</vue-good-table>
```

<checkbox-table />


## Selected row action slot
Once you select a row, an info bar shows up. This bar allows for a customizable slot for your action buttons. 

### Example

```html
<vue-good-table
  @on-selected-rows-change="selectionChanged"
  :columns="columns"
  :rows="rows"
  :select-options="{ 
    enabled: true,
  }"
  :search-options="{ enabled: true }">
  <div slot="selected-row-actions">
    <button>Action 1</button>
  </div>
</vue-good-table>
<!-- click on a row below to show the action button -->
```

<checkbox-table :show-slot="true" />

::: tip Note
You can style the selection info bar by supplying a css class to `selectionInfoClass` property.
:::