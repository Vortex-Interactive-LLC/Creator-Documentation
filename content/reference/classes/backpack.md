---
title: Backpack
description: Stores the tools a player is not holding.
---

## Summary

Every [`Player`](./player.md) has a `Backpack`, available as `player.Backpack`. It holds the [`Tool`](./tool.md)s the player owns but is not holding. It is created for the player when they join, and filled with copies of the tools in [`StarterPack`](./starter-pack.md). See the [Tools & the Backpack guide](../../guides/tools-and-backpack.md).

### Example

```luau
local copy = tool:Clone()
copy.Parent = player.Backpack
```

## Notes

`GetChildren` and `FindFirstChild` list the tools in the backpack. A tool that is equipped is a child of the character, not of the backpack. The backpack is emptied and refilled from `StarterPack` when the player respawns.
