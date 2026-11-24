---
title: Weld
description: Holds two parts together at an offset you choose.
---

## Summary

A `Weld` joins `Part0` and `Part1` so they move as one, and places `Part1` using the offsets `C0` and `C1`. Where a [`WeldConstraint`](./weld-constraint.md) keeps the distance the parts already have, a `Weld` moves the parts to the position its offsets describe. Welded parts share one assembly, see [`AssemblyRootPart`](./part.md#assemblyrootpart).

```luau
local weld = Instance.new("Weld")
weld.Part0 = body
weld.Part1 = handle
weld.C0 = CFrame.new(0, 1, 0)
weld.Parent = body
```

## Properties

- `Part0` - [`Part`](./part.md) | `nil`, the first part. Defaults to `nil`;
- `Part1` - [`Part`](./part.md) | `nil`, the second part. Defaults to `nil`;
- `C0` - [`CFrame`](../datatypes/cframe.md), where the weld sits relative to `Part0`. Defaults to the identity `CFrame`;
- `C1` - [`CFrame`](../datatypes/cframe.md), where the weld sits relative to `Part1`. Defaults to the identity `CFrame`. The parts are placed so that `Part0.CFrame * C0` is equal to `Part1.CFrame * C1`;
- `Enabled` - `boolean`, defaults to `true`. When `false` the parts are not held together;
- `Active` - `boolean`, read-only. `true` while the weld is joining its two parts;
- `Name`, `ClassName`, `Parent`.
