---
title: UIPadding
description: Insets the children of the GUI object it is inside.
---

## Summary

Place a `UIPadding` inside a GUI object to keep its children away from its edges. Scale values are a fraction of the parent's size.

```luau
local padding = Instance.new("UIPadding")
padding.PaddingLeft = UDim.new(0, 10)
padding.PaddingTop = UDim.new(0, 10)
padding.Parent = frame
```

## Properties

- `PaddingTop`, `PaddingBottom`, `PaddingLeft`, `PaddingRight` - [`UDim`](../datatypes/udim.md), each defaults to `0, 0`;
- `Name`, `ClassName`, `Parent`.
