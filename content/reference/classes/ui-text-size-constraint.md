---
title: UITextSizeConstraint
description: Limits the size of the text of the GUI object it is inside.
---

## Summary

Place a `UITextSizeConstraint` inside a text object to keep its text size between two values. It limits `TextSize` and the size `TextScaled` picks, after any [`UIScale`](./ui-scale.md).

```luau
local limit = Instance.new("UITextSizeConstraint")
limit.MinTextSize = 12
limit.MaxTextSize = 40
limit.Parent = label
```

## Properties

- `MinTextSize` - `number`, defaults to `1`;
- `MaxTextSize` - `number`, defaults to `100`. If it is smaller than `MinTextSize`, `MinTextSize` wins;
- `Name`, `ClassName`, `Parent`.
