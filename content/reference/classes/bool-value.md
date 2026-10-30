---
title: BoolValue
description: An unsupported Roblox-compatible boolean value container.
---

## Summary

`BoolValue` stores a boolean `Value`. It can be constructed in both `Script` and `LocalScript` and does not need a parent for its value to be read or written.

## Properties

### Name

> `string`

The name of the instance. A new value is named `BoolValue`.

### Value

> `boolean`

A new `BoolValue` starts at `false`.

```lua
local flag = Instance.new("BoolValue")
flag.Value = true
print(flag.Value) -- true
```

## Change notifications

`Changed` and `GetPropertyChangedSignal("Value")` fire after `Value` is assigned.
