---
title: Sparkles
description: Twinkling sparkles around a part.
---

## Summary

A `Sparkles` makes small twinkling lights appear around the part it is parented to.

```luau
local sparkles = Instance.new("Sparkles")
sparkles.SparkleColor = Color3.new(1, 0.8, 0.2)
sparkles.Parent = workspace.Crystal
```

## Properties

- `SparkleColor` - [`Color3`](../datatypes/color3.md), defaults to purple;
- `Enabled` - `boolean`, defaults to `true`;
- `TimeScale` - `number` from `0` to `100`, speed of the effect. Defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Sparkles are drawn on the client;
- For more control, use a [`ParticleEmitter`](./particle-emitter.md).
