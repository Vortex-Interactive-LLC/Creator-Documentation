---
title: TweenInfo
description: Global constructor for TweenInfo animation configuration.
---

`TweenInfo` is the global constructor used to configure a Tween.

```luau
local info = TweenInfo.new(
    1,
    Enum.EasingStyle.Linear,
    Enum.EasingDirection.In,
    -1,
    false,
    0
)
```

Set the `repeatCount` argument to `-1` to repeat forever. See the full [TweenInfo datatype reference](../datatypes/tween-info.md).
