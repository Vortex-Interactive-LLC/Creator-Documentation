---
title: UIScale
description: Scales the GUI object it is inside and everything in that object.
---

## Summary

Place a `UIScale` inside a GUI object to multiply the size of that object and of everything inside it. Pixel offsets, text size, `UIStroke` thickness, `UIPadding`, `UIListLayout` padding, and the `UICorner` offset all grow with it. Use it to resize a whole panel with one number.

```luau
local scale = Instance.new("UIScale")
scale.Scale = 1.5
scale.Parent = panel
```

The object keeps its `Position` and `AnchorPoint`, so it grows from its anchor point. Scales inside scales multiply. `AbsoluteSize` reports the scaled size.

## Properties

- `Scale` - `number`, defaults to `1`. Values are limited to `0` through `100`;
- `Name`, `ClassName`, `Parent`.
