---
title: SunRaysEffect
description: Draws light shafts streaming from the sun.
---

## Summary

A `SunRaysEffect` draws light shafts streaming away from the sun when it is on screen. Put it in [`Lighting`](./lighting.md).

```luau
local rays = Instance.new("SunRaysEffect")
rays.Intensity = 0.4
rays.Parent = game:GetService("Lighting")
```

## Properties

- `Enabled` - `boolean`, defaults to `true`;
- `Intensity` - `number` from `0` to `1`, how strong the shafts are. Defaults to `0.25`;
- `Spread` - `number` from `0` to `1`, how far the shafts reach across the screen. Defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

- The shafts fade out when the sun is behind you or below the horizon;
- Anything bright near the sun's direction adds to the shafts, and parts in front of the sun block them;
- Sun rays do not draw on the OpenGL backend;
- Only the first enabled `SunRaysEffect` in `Lighting` is used.
