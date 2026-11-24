---
title: WeldConstraint
description: Holds two parts together at the distance they are from each other.
---

## Summary

A `WeldConstraint` joins `Part0` and `Part1` so they move as one. The parts stay in the position and rotation they had relative to each other when the constraint was connected. Welded parts share one assembly, see [`AssemblyRootPart`](./part.md#assemblyrootpart).

```luau
local weld = Instance.new("WeldConstraint")
weld.Part0 = base
weld.Part1 = wheel
weld.Parent = base
```

## Properties

- `Part0` - [`Part`](./part.md) | `nil`, the first part. Defaults to `nil`;
- `Part1` - [`Part`](./part.md) | `nil`, the second part. Defaults to `nil`;
- `Enabled` - `boolean`, defaults to `true`. When `false` the parts are not held together;
- `Active` - `boolean`, read-only. `true` while the constraint is joining its two parts;
- `Name`, `ClassName`, `Parent`.
