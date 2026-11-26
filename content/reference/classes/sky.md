---
title: Sky
description: Replaces the sky with a skybox and sets the stars and celestial bodies.
---

## Summary

A `Sky` placed in [`Lighting`](./lighting.md) changes how the sky looks. Give it six images to draw a skybox, or leave the faces empty to keep the built-in day and night sky.

```luau
local sky = Instance.new("Sky")
sky.StarCount = 1500
sky.SunAngularSize = 30
sky.Parent = game:GetService("Lighting")
```

## Properties

- `SkyboxBk`, `SkyboxDn`, `SkyboxFt`, `SkyboxLf`, `SkyboxRt`, `SkyboxUp` - `number`, image asset ids for the back, down, front, left, right and up faces. A face left at `0` shows the built-in sky;
- `StarCount` - `number` from `0` to `5000`. Defaults to `3000`;
- `CelestialBodiesShown` - `boolean`, whether the sun and moon are drawn. Defaults to `true`;
- `SunAngularSize` - `number` from `0` to `60`. Defaults to `21`;
- `MoonAngularSize` - `number` from `0` to `60`. Defaults to `11`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Only the first `Sky` in `Lighting` is used;
- The sun, moon and stars are drawn over the skybox;
- Sun and moon textures are not supported.
