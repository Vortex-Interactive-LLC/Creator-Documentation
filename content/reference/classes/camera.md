---
title: Camera
description: The player's view of the world.
---

## Summary

The current camera is available as `workspace.CurrentCamera` in a `LocalScript`. See the [Mouse & Camera guide](../../guides/mouse-and-camera.md).

### Example

```luau
-- LocalScript
local camera = workspace.CurrentCamera

camera.CameraType = Enum.CameraType.Scriptable
camera.CFrame = CFrame.lookAt(Vector3.new(0, 60, 80), Vector3.new(0, 0, 0))
camera.FieldOfView = 50
```

## Properties

- `CameraType` - `Enum.CameraType`, defaults to `Custom`. `Custom` is the default camera that follows the character. `Scriptable` and `Fixed` stop it and keep the view where it is, until a script sets `CFrame`;
- `CFrame` - [`CFrame`](../datatypes/cframe.md), the camera position and orientation. Writing it moves the camera while `CameraType` is `Scriptable` or `Fixed`. While it is `Custom`, the default camera overwrites it;
- `FieldOfView` - `number`, the vertical field of view in degrees. Defaults to `70`. Values are clamped to `1` to `120`;
- `ViewportSize` - [`Vector2`](../datatypes/vector2.md), the size of the game view in pixels. Read-only;
- `Name`, `ClassName` - `"Camera"`.

All other members are read-only; writing one raises an error. `CameraType` accepts only an `Enum.CameraType`, `CFrame` only a `CFrame`, and `FieldOfView` only a number.

## Methods

- `ScreenPointToRay(x: number, y: number, depth: number?)` - returns a ray through that screen position. `Origin` is the camera position moved forward by `depth` (default `0`) and `Direction` is a unit vector;
- `ViewportPointToRay(x, y, depth?)` - the same method.

## Notes

In Studio, the `Camera` under `Workspace` in the Explorer sets the starting `CameraType` and `FieldOfView` for the game. A `Scriptable` or `Fixed` camera starts frozen at the default view until a script sets `CFrame`.

A write is visible to reads in the same frame, so a camera that follows something every `RenderStepped` does not lag behind it.

While `CameraType` is not `Custom`, the default mouse look and zoom do not move the camera. Movement keys still move the character relative to the direction the camera faces. Setting `CameraType` back to `Custom` returns the camera to the default one, which continues from the last direction it faced.

Only the local player's camera can be scripted.
