---
title: IntValue
description: A detached integer value container.
---

## Summary

`IntValue` can be constructed in both `Script` and `LocalScript`. It stores a numeric `Value` and does not need a parent for its value to be read or written.

## Properties

### Name

> `string`

The name of the instance. A new value is named `IntValue`.

### Value

> `number`

A new `IntValue` starts at `0`. Assigning and reading integer values works:

```lua
local score = Instance.new("IntValue")
score.Value = 42
print(score.Value) -- 42
```

## Change notifications

`Changed` and `GetPropertyChangedSignal("Value")` fire after `Value` is assigned, once the `IntValue` is parented into the game. Fractional numbers are truncated to an integer (`3.7` becomes `3`).
