---
title: BloomEffect
description: Makes bright parts of the screen glow.
---

## Summary

A `BloomEffect` makes the brightest parts of the screen glow. Put it in [`Lighting`](./lighting.md).

```luau
local bloom = Instance.new("BloomEffect")
bloom.Intensity = 0.6
bloom.Parent = game:GetService("Lighting")
```

## Properties

- `Enabled` - `boolean`, defaults to `true`. A disabled `BloomEffect` turns bloom off;
- `Intensity` - `number` from `0` to `1`, how strong the glow is. Defaults to `0.4`;
- `Size` - `number` from `0` to `56`, how far the glow spreads. Defaults to `24`;
- `Threshold` - `number`, how bright a pixel has to be before it glows. Defaults to `0.95`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Bloom only draws at the two highest graphics qualities, and not on the OpenGL backend;
- Without a `BloomEffect`, those qualities still draw a default bloom that makes `Neon` and `ForceField` parts glow. Add a disabled `BloomEffect` to turn that off;
- Only the first `BloomEffect` in `Lighting` is used.
