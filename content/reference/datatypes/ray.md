---
title: Ray
description: An origin and a direction in the world.
---

## Summary

A `Ray` is returned by [`Mouse.UnitRay`](../classes/mouse.md) and [`Camera:ScreenPointToRay`](../classes/camera.md). There is no `Ray` constructor.

```lua
local ray = workspace.CurrentCamera:ScreenPointToRay(mouse.X, mouse.Y)
local result = workspace:Raycast(ray.Origin, ray.Direction * 500)
```

## Properties

- `Origin` - [`Vector3`](./vector3.md), where the ray starts;
- `Direction` - [`Vector3`](./vector3.md), a unit vector for the way the ray points;
- `Unit` - the ray itself.

Multiply `Direction` by a distance to use it with [`workspace:Raycast`](../classes/workspace.md).
