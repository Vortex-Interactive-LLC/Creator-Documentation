---
title: Values
description: Store simple script-visible values in Vortex.
---
> [!Summary]
> Values are simple containers used to store small pieces of state like counters or labels. Vortex provides `IntValue`, `NumberValue`, `StringValue`, and `BoolValue`.

## Available containers

| Class | Stores | Default |
| --- | --- | --- |
| [`IntValue`](../reference/classes/int-value.md) | An integer. Fractional values are truncated (`3.7` becomes `3`). | `0` |
| `NumberValue` | Any number. | `0` |
| [`StringValue`](../reference/classes/string-value.md) | A string. | `""` |
| [`BoolValue`](../reference/classes/bool-value.md) | A boolean. | `false` |

Their `Value` properties are readable and writable in both Script and LocalScript.

```lua
local coins = Instance.new("IntValue")
coins.Value = 25

local status = Instance.new("StringValue")
status.Value = "ready"

local isVip = Instance.new("BoolValue")
isVip.Value = true
```

Values placed in a `leaderstats` folder on a player are shown on the leaderboard. See [Leaderboards](./leaderboard.md).

## Observing changes

`Changed` and `GetPropertyChangedSignal("Value")` fire after `Value` is assigned. They work on any value object, whether or not it has a parent yet. `Changed` passes the new value. Assigning the value it already holds does not fire them.
