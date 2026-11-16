---
title: StarterPlayer
description: The default camera and character settings for every player in a game.
---

## Summary

`StarterPlayer` holds the starting camera and character settings for every player. It appears in the Studio Explorer under `Workspace`, and its properties are set in Studio's Properties panel. A `LocalScript` can reach it with `game:GetService("StarterPlayer")`.

`StarterPlayer` cannot be created or destroyed.

### Example

```luau
-- LocalScript
local starter = game:GetService("StarterPlayer")

starter.CameraMaxZoomDistance = 40
starter.CameraMode = Enum.CameraMode.LockFirstPerson
```

## Properties

- `CameraMaxZoomDistance` - `number` from `0.5` to `400`, how far the camera can zoom out. Defaults to `128`;
- `CameraMinZoomDistance` - `number` from `0.5` to `400`, how close the camera can zoom in. Defaults to `1`, which is first person. Cannot be above `CameraMaxZoomDistance`;
- `CameraMode` - `Enum.CameraMode`, defaults to `Classic`. `LockFirstPerson` keeps the camera in first person and turns zooming off;
- `EnableMouseLockOption` - `boolean`, defaults to `true`. When `false`, shift lock cannot be turned on, and it is turned off if it was on;
- `CharacterWalkSpeed` - `number` from `0` to `1000`, the starting walk speed of a character. Defaults to `16`;
- `CharacterJumpPower` - `number` from `0` to `1000`, the starting jump power of a character. Defaults to `50`;
- `Name`, `ClassName` - `"StarterPlayer"`.

Values outside the range are clamped, and raising `CameraMinZoomDistance` above `CameraMaxZoomDistance` raises the maximum with it. All other members are read-only; writing one raises an error.

## Notes

`CharacterWalkSpeed` and `CharacterJumpPower` apply to characters spawned after the change. To change a character that already exists, set `WalkSpeed` and `JumpPower` on its [`Humanoid`](./humanoid.md).

Scripts can only change these settings from a `LocalScript`, and the change applies to that player alone. `GetService("StarterPlayer")` raises an error in a server `Script`.
