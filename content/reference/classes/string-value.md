---
title: StringValue
description: A detached string value container.
---

## Summary

`StringValue` can be constructed in Vortex Studio 0.3.4 in both `Script` and
`LocalScript` contexts. It stores a string `Value` and does not need a parent for its 
value to be read or written.
## Properties

### Name

> `string`

The instance name. A new `StringValue` is named `StringValue` by default.

### Value

> `string`

A new `StringValue` starts with an empty string. Assigning and reading string
values works:

```lua
local message = Instance.new("StringValue")
message.Value = "Hello, Vortex"
print(message.Value) -- Hello, Vortex
```

## Change notifications

`Changed` and `GetPropertyChangedSignal("Value")` are present and connectable,
but changing `Value` did not trigger either callback in the tested 0.3.4 runtime.
runtime. Poll `Value` when a script must observe a change.
