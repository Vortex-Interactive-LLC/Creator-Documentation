---
title: Atmosphere
description: Adds distance haze that replaces the fog settings of Lighting.
---

## Summary

An `Atmosphere` placed in [`Lighting`](./lighting.md) fades distant parts into a haze. While one exists, it replaces `Lighting.FogStart`, `FogEnd` and `FogColor`.

```luau
local atmosphere = Instance.new("Atmosphere")
atmosphere.Density = 0.3
atmosphere.Color = Color3.fromRGB(190, 200, 220)
atmosphere.Parent = game:GetService("Lighting")
```

## Properties

- `Density` - `number` from `0` to `1`. Higher values bring the haze closer. Defaults to `0.395`;
- `Color` - [`Color3`](../datatypes/color3.md), the haze color. It is mixed with the sky color and darkens at night;
- `Haze` - `number` from `0` to `10`, extra haze on top of `Density`. Defaults to `0`;
- `Offset`, `Decay`, `Glare` - accepted and saved, but they do not change the picture yet;
- `Name`, `ClassName`, `Parent`.

## Notes

- Only the first `Atmosphere` in `Lighting` is used;
- This is a fog approximation, not a light-scattering sky.
