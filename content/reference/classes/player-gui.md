---
title: PlayerGui
description: Holds a player's copy of the GUIs in StarterGui.
---

## Summary

Each player has a `PlayerGui`, a child of their [`Player`](./player.md). When the player joins it is filled with copies of everything in [`StarterGui`](./starter-gui.md), including `LocalScript`s. It is created on the player's own client, so `player.PlayerGui` is `nil` in a server `Script`.

```luau
-- LocalScript
local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
local hud = playerGui:FindFirstChild("Hud")
```

A [`ScreenGui`](./screen-gui.md) with `ResetOnSpawn` set to `true` is replaced with a fresh copy from `StarterGui` each time the player's character respawns. See [Building GUIs](../../guides/gui.md).
