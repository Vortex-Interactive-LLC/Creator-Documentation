---
title: ColorCorrectionEffect
description: Changes the brightness, contrast, saturation and tint of the whole screen.
---

## Summary

A `ColorCorrectionEffect` changes how the whole screen looks. Put it in [`Lighting`](./lighting.md).

```luau
local correction = Instance.new("ColorCorrectionEffect")
correction.Saturation = -0.5
correction.TintColor = Color3.fromRGB(255, 220, 190)
correction.Parent = game:GetService("Lighting")
```

## Properties

- `Enabled` - `boolean`, defaults to `true`;
- `Brightness` - `number` from `-1` to `1`. Defaults to `0`;
- `Contrast` - `number` from `-1` to `1`. Defaults to `0`;
- `Saturation` - `number` from `-1` to `1`. `-1` is black and white. Defaults to `0`;
- `TintColor` - [`Color3`](../datatypes/color3.md), defaults to white;
- `Name`, `ClassName`, `Parent`.

## Notes

- It works at every graphics quality;
- Several enabled `ColorCorrectionEffect` objects in `Lighting` add together;
- `TintColor` is approximated with a warm to cool and green to magenta shift, so strong tints are not exact.
