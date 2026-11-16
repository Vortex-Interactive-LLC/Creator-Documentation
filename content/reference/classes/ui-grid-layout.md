---
title: UIGridLayout
description: Arranges the children of a GUI object in a grid of equal cells.
---

## Summary

Place a `UIGridLayout` inside a GUI object to lay its children out in rows or columns of equal cells, like an inventory or shop. Every child is given the size of a cell, so its own `Size` and `Position` are ignored. Children with `Visible` set to `false` are skipped. The grid wraps to a new line when the next cell would not fit.

```luau
local grid = Instance.new("UIGridLayout")
grid.CellSize = UDim2.fromOffset(100, 100)
grid.CellPadding = UDim2.fromOffset(8, 8)
grid.Parent = frame
```

## Properties

- `CellSize` - [`UDim2`](../datatypes/udim2.md), the size of each cell, with scale taken from the parent's size. Defaults to `0, 100, 0, 100`;
- `CellPadding` - [`UDim2`](../datatypes/udim2.md), the gap between cells. Defaults to `0, 5, 0, 5`;
- `FillDirection` - `Enum.FillDirection`: `Horizontal` fills a row before starting the next, `Vertical` fills a column before starting the next. Defaults to `Horizontal`;
- `FillDirectionMaxCells` - `number`, the most cells on a line. `0` means as many as fit. Defaults to `0`;
- `StartCorner` - `Enum.StartCorner`: `TopLeft`, `TopRight`, `BottomLeft`, or `BottomRight`. The corner the first cell goes in. Defaults to `TopLeft`;
- `HorizontalAlignment` - `Enum.HorizontalAlignment`: `Left`, `Center`, or `Right`. Aligns each line, or the whole grid, along the horizontal axis. Defaults to `Left`;
- `VerticalAlignment` - `Enum.VerticalAlignment`: `Top`, `Center`, or `Bottom`. Defaults to `Top`;
- `SortOrder` - `Enum.SortOrder`: `LayoutOrder` sorts by each child's `LayoutOrder`, `Name` sorts by name. Defaults to `LayoutOrder`;
- `Name`, `ClassName`, `Parent`.

A [`UISizeConstraint`](./ui-size-constraint.md) or [`UIAspectRatioConstraint`](./ui-aspect-ratio-constraint.md) inside a child can make it smaller than its cell. If a frame has both a `UIListLayout` and a `UIGridLayout`, the list is used.
