---
title: Values
description: Store simple script-visible values in Vortex.
---
> [!Summary]
> Values are simple script-visible containers used to store small pieces of state like counters or labels.

## Available containers

Vortex Studio 0.3.4 supports detached [`IntValue`](../reference/classes/int-value.md), [`StringValue`](../reference/classes/string-value.md), `NumberValue` and `BoolValue` instances.
They start at `0`, `""`, `0`, `false` respectively, and their `Value` properties are
readable and writable in both Script and LocalScript.

## Code Samples

```lua
local coins = Instance.new("IntValue")
coins.Value = 25

local status = Instance.new("StringValue")
status.Value = "ready"

local state = Instance.new("BoolValue")
state.Value = true

local fuel = Instance.new("NumberValue")
fuel.Value = 10.5
```

## Observing changes

The value instances expose `Changed` and
`GetPropertyChangedSignal("Value")`, but neither delivered callbacks after a
`Value` assignment in the tested runtime. Read or poll `Value` instead of
using these signals for game logic.
