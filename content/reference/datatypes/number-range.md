---
title: NumberRange
description: A minimum and a maximum number.
---

## Summary

A `NumberRange` holds a minimum and a maximum. Properties such as a `ParticleEmitter`'s `Lifetime` and `Speed` use it to pick a random value between the two for every particle.

```lua
local range = NumberRange.new(1, 3)
print(range.Min, range.Max) -- 1 3
```

## Constructors

- `NumberRange.new(value: number)` - a range where `Min` and `Max` are both `value`;
- `NumberRange.new(min: number, max: number)` - errors if `min` is greater than `max`.

## Properties

- `Min` - `number`, the lowest value, read-only;
- `Max` - `number`, the highest value, read-only.

## Operators

`==` between two `NumberRange`s.
