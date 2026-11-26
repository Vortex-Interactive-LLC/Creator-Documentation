---
title: BlurEffect
description: Blurs the whole screen.
---

## Summary

A `BlurEffect` blurs everything on the screen. Put it in [`Lighting`](./lighting.md).

```luau
local blur = Instance.new("BlurEffect")
blur.Size = 16
blur.Parent = game:GetService("Lighting")
```

## Properties

- `Enabled` - `boolean`, defaults to `true`;
- `Size` - `number` from `0` to `56`, how far the blur spreads in pixels. Defaults to `24`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Blur does not draw on the OpenGL backend;
- Only the first enabled `BlurEffect` in `Lighting` is used.
