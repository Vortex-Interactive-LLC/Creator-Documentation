---
title: Mouse
description: The cursor of the local player, and what it points at in the world.
---

## Summary

Returned by `Player:GetMouse()`. Available only to the `LocalPlayer` in a `LocalScript`. See the [Mouse & Camera guide](../../guides/mouse-and-camera.md).

### Example

```luau
-- LocalScript
local mouse = game:GetService("Players").LocalPlayer:GetMouse()

mouse.Button1Down:Connect(function()
    print(mouse.Target, mouse.Hit.Position)
end)
```

## Properties

- `X`, `Y` - `number`, cursor position in pixels;
- `ViewSizeX`, `ViewSizeY` - `number`, size of the game view in pixels;
- `Hit` - [`CFrame`](../datatypes/cframe.md), the world point under the cursor;
- `Target` - the part under the cursor, or `nil`;
- `Origin` - [`CFrame`](../datatypes/cframe.md), the camera-side start of the cursor ray;
- `UnitRay` - the ray from the camera through the cursor;
- `TargetFilter` - an instance that `Hit` and `Target` ignore. Writable;
- `Icon` - writable.

All other members are read-only; writing one raises an error.

## Signals

`Button1Down`, `Button1Up`, `Button2Down`, `Button2Up` and `Move`.
