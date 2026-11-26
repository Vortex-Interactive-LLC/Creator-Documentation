---
title: Smoke
description: Puffs of smoke rising from a part.
---

## Summary

A `Smoke` makes soft puffs of smoke drift up from the part it is parented to.

```luau
local smoke = Instance.new("Smoke")
smoke.Size = 3
smoke.Opacity = 0.7
smoke.RiseVelocity = 4
smoke.Parent = workspace.Chimney
```

## Properties

- `Color` - [`Color3`](../datatypes/color3.md), defaults to grey;
- `Opacity` - `number` from `0` to `1`, how solid the smoke is. Defaults to `0.5`;
- `RiseVelocity` - `number` from `-25` to `25`, how fast the smoke rises. Negative values sink. Defaults to `1`;
- `Size` - `number` from `0.1` to `100`, defaults to `1`;
- `Enabled` - `boolean`, defaults to `true`;
- `TimeScale` - `number` from `0` to `100`, speed of the effect. Defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Smoke is drawn on the client;
- For more control, use a [`ParticleEmitter`](./particle-emitter.md).
