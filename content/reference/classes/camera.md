---
title: Camera
description: The player's view of the world.
---

## Summary

The current camera is available as `workspace.CurrentCamera` in a `LocalScript`. See the [Mouse & Camera guide](../../guides/mouse-and-camera.md).

## Properties

- `CFrame` - [`CFrame`](../datatypes/cframe.md), the camera position and orientation. Scripts cannot move the camera;
- `ViewportSize` - [`Vector2`](../datatypes/vector2.md), the size of the game view in pixels;
- `Name`, `ClassName` - `"Camera"`.

## Methods

- `ScreenPointToRay(x: number, y: number, depth: number?)` - returns a ray through that screen position. `Origin` is the camera position moved forward by `depth` (default `0`) and `Direction` is a unit vector;
- `ViewportPointToRay(x, y, depth?)` - the same method.

## Notes

The camera table is a snapshot taken when `workspace.CurrentCamera` is read. Read it again to see the current position.
