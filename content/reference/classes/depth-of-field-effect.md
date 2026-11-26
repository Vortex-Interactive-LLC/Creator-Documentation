---
title: DepthOfFieldEffect
description: Blurs things that are closer or farther than the focus distance.
---

## Summary

A `DepthOfFieldEffect` blurs everything that is not at the focus distance. Put it in [`Lighting`](./lighting.md).

```luau
local focus = Instance.new("DepthOfFieldEffect")
focus.FocusDistance = 30
focus.InFocusRadius = 15
focus.Parent = game:GetService("Lighting")
```

## Properties

- `Enabled` - `boolean`, defaults to `true`;
- `FocusDistance` - `number`, studs from the camera to what is in focus. Defaults to `0`;
- `InFocusRadius` - `number`, studs around the focus distance that stay sharp. Defaults to `10`;
- `FarIntensity` - `number` from `0` to `1`, how much things behind the focus blur. Defaults to `0.75`;
- `NearIntensity` - `number` from `0` to `1`, how much things in front of the focus blur. Defaults to `0.75`;
- `Name`, `ClassName`, `Parent`.

## Notes

- Depth of field only draws at the highest graphics quality, and not on the OpenGL backend;
- The blur is a lens approximation, so `FarIntensity` and `NearIntensity` act as one strength (the larger of the two) and `InFocusRadius` shifts the focus distance;
- Only the first enabled `DepthOfFieldEffect` in `Lighting` is used.
