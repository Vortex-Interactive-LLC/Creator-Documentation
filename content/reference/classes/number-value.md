---
title: NumberValue
description: Stores a number.
---

## Summary

A `NumberValue` stores a number in its `Value` property. Unlike an [`IntValue`](./int-value.md), it keeps fractional values.

```lua
local speed = Instance.new("NumberValue")
speed.Value = 3.7
print(speed.Value) --> 3.7
```

## Properties

- `Value` - `number`, starts at `0`;
- `Name`, `ClassName`, `Parent`.

Like the other value objects it is useful as a stat under a player's `leaderstats` folder. See [Leaderboards](../../guides/leaderboard.md).

## Change notifications

`Changed` and `GetPropertyChangedSignal("Value")` fire after `Value` is assigned.
