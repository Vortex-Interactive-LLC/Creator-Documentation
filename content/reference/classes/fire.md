---
title: Fire
description: A flame that burns on a part.
---

## Summary

A `Fire` makes a flame rise from the part it is parented to.

```luau
local fire = Instance.new("Fire")
fire.Size = 8
fire.Heat = 12
fire.Color = Color3.new(1, 0.6, 0.2)
fire.SecondaryColor = Color3.new(0.6, 0.1, 0)
fire.Parent = workspace.Torch
```

## Properties

- `Color` - [`Color3`](../datatypes/color3.md), the main flame color. Defaults to orange;
- `SecondaryColor` - [`Color3`](../datatypes/color3.md), the color the flame fades to. Defaults to a dark red-brown;
- `Heat` - `number` from `-25` to `25`, how fast the flame rises. Defaults to `9`;
- `Size` - `number` from `2` to `30`, how big the flame is. Defaults to `5`;
- `Enabled` - `boolean`, defaults to `true`;
- `TimeScale` - `number` from `0` to `100`, speed of the effect. Defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Fire is drawn on the client and does not damage anything;
- For more control, use a [`ParticleEmitter`](./particle-emitter.md).
