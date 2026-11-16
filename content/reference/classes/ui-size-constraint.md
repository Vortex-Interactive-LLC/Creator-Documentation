---
title: UISizeConstraint
description: Limits how small or large the GUI object it is inside can be.
---

## Summary

Place a `UISizeConstraint` inside a GUI object to clamp its size in pixels, however its `Size` is set. Use it to keep a panel from getting tiny on a small window or huge on a large one. It applies after [`UIScale`](./ui-scale.md) and [`UIAspectRatioConstraint`](./ui-aspect-ratio-constraint.md).

```luau
local limit = Instance.new("UISizeConstraint")
limit.MinSize = Vector2.new(200, 100)
limit.MaxSize = Vector2.new(600, 400)
limit.Parent = panel
```

## Properties

- `MinSize` - [`Vector2`](../datatypes/vector2.md), the smallest size in pixels. Defaults to `0, 0`;
- `MaxSize` - [`Vector2`](../datatypes/vector2.md), the largest size in pixels. Defaults to `100000, 100000`, so `math.huge` works for no limit. If it is smaller than `MinSize`, `MinSize` wins;
- `Name`, `ClassName`, `Parent`.
