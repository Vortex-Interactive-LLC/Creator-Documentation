---
title: StarterPack
description: A service whose tools are copied into every player's backpack.
---

## Summary

Tools placed inside `StarterPack` are copied into each player's [`Backpack`](./backpack.md) when they join and every time they respawn. Get it with `game:GetService("StarterPack")`. See the [Tools & the Backpack guide](../../guides/tools-and-backpack.md).

### Example

```luau
local tool = Instance.new("Tool")
tool.Name = "Torch"
tool.Parent = game:GetService("StarterPack")
```
