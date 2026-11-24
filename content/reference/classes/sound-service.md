---
title: SoundService
description: Controls how sounds in the world are heard.
---

## Summary

`SoundService` holds the settings for sounds that are played in the world, and plays a sound for the local player only. Get it with `game:GetService("SoundService")`. See [`Sound`](./sound.md).

```luau
-- LocalScript
local SoundService = game:GetService("SoundService")

SoundService:PlayLocalSound(script.Parent.Click)
```

## Properties

- `RolloffScale` - `number` from `0` to `100`, defaults to `1`. How fast the volume of a sound falls off with distance. Larger values make sounds fade sooner;
- `Name`, `ClassName`.

## Methods

### PlayLocalSound

> `SoundService:PlayLocalSound(sound: Sound)`

Plays `sound` for the local player only. `LocalScript` only: calling it from a server `Script` raises an error.
