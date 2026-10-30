---
title: UIListLayout
description: Stacks the children of a GUI object in a row or column.
---

## Summary

Place a `UIListLayout` inside a GUI object to arrange its children one after another. The children's `Position` is ignored, and children with `Visible` set to `false` are skipped.

```luau
local list = Instance.new("UIListLayout")
list.FillDirection = Enum.FillDirection.Vertical
list.Padding = UDim.new(0, 6)
list.Parent = frame
```

## Properties

- `FillDirection` - `Enum.FillDirection`: `Vertical` or `Horizontal`. Defaults to `Vertical`;
- `HorizontalAlignment` - `Enum.HorizontalAlignment`: `Left`, `Center` or `Right`. Defaults to `Left`;
- `VerticalAlignment` - `Enum.VerticalAlignment`: `Top`, `Center` or `Bottom`. Defaults to `Top`;
- `SortOrder` - `Enum.SortOrder`: `LayoutOrder` sorts by each child's `LayoutOrder`, `Name` sorts by name. Defaults to `LayoutOrder`;
- `Padding` - [`UDim`](../datatypes/udim.md), the gap between children. Defaults to `0, 0`;
- `Name`, `ClassName`, `Parent`.
