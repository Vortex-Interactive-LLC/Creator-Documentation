---
title: StringValue
description: A detached string value container.
---

## Summary

`StringValue` can be constructed in both `Script` and `LocalScript` contexts. It stores a string `Value` and does not need a parent for its value to be read or written.

## Properties

### Name

> `string`

The instance name. A new `StringValue` is named `StringValue` by default.

### Value

> `string`

A new `StringValue` starts with an empty string. Assigning and reading string values works:

```lua
local message = Instance.new("StringValue")
message.Value = "Hello, Vortex"
print(message.Value) -- Hello, Vortex
```

## Change notifications

`Changed` and `GetPropertyChangedSignal("Value")` fire after `Value` is assigned.
