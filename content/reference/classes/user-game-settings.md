---
title: UserGameSettings
description: Reports the player's own game settings.
---

## Summary

`UserGameSettings` holds the settings of the local player. Use it in a `LocalScript` with `game:GetService("UserGameSettings")`.

## Properties

- `MouseSensitivity` - `number`, read-only. How sensitive the mouse is when the camera is turned with it. Defaults to `1`;
- `ControlMode` - `Enum.ControlMode`, read-only. `Classic` or `MouseLockSwitch`. Defaults to `MouseLockSwitch`, which lets the player turn shift lock on and off;
- `RotationType` - `Enum.RotationType`: `MovementRelative` turns the character toward the direction it walks, and `CameraRelative` keeps the character facing where the camera faces. Defaults to `MovementRelative`;
- `Name`, `ClassName`.
