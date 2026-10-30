---
title: UICorner
description: Rounds the corners of the GUI object it is inside.
---

## Summary

Place a `UICorner` inside a [`Frame`](./frame.md), [`TextLabel`](./text-label.md), [`TextButton`](./text-button.md) or [`ImageLabel`](./image-label.md) to round its corners.

```luau
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = frame
```

## Properties

- `CornerRadius` - [`UDim`](../datatypes/udim.md), the radius of the corners. Defaults to `0, 8`;
- `Name`, `ClassName`, `Parent`.
