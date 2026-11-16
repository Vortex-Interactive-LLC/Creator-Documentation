---
title: UIAspectRatioConstraint
description: Keeps the GUI object it is inside at a fixed width to height ratio.
---

## Summary

Place a `UIAspectRatioConstraint` inside a GUI object to keep its width divided by its height at `AspectRatio`. It adjusts the size that `Size` resolves to, so the object stays square, or 16:9, as the window changes.

```luau
local ratio = Instance.new("UIAspectRatioConstraint")
ratio.AspectRatio = 1
ratio.Parent = icon
```

## Properties

- `AspectRatio` - `number`, width divided by height. Defaults to `1`. Values of `0` or less are ignored;
- `AspectType` - `Enum.AspectType`: `FitWithinMaxSize` shrinks the object to the largest size with that ratio that fits inside its normal size, and `ScaleWithParentSize` takes one axis from the normal size and works out the other, so the object can be larger than `Size`. Defaults to `FitWithinMaxSize`;
- `DominantAxis` - `Enum.DominantAxis`: with `ScaleWithParentSize`, `Width` keeps the width and works out the height, and `Height` does the opposite. Defaults to `Width`;
- `Name`, `ClassName`, `Parent`.
