---
title: Tool
description: An item a player can hold.
---

## Summary

A `Tool` is held when its parent is a player's character, and stored when its parent is the player's [`Backpack`](./backpack.md). Tools placed in [`StarterPack`](./starter-pack.md) are given to every player. See the [Tools & the Backpack guide](../../guides/tools-and-backpack.md).

### Example

```luau
local tool = Instance.new("Tool")
tool.Name = "Sword"
tool.Parent = game:GetService("StarterPack")

tool.Activated:Connect(function()
    print("used")
end)
```

## Properties

- `CanBeDropped` - `Boolean`, defaults to `true`;
- `RequiresHandle` - `Boolean`, defaults to `true`;
- `ToolTip` - `string`, empty by default;
- `TextureId` - `number`, defaults to `0`;
- `Grip`, `GripPos` - how the tool is positioned in the hand;
- `Name`, `ClassName`, `Parent`.

## Signals

- `Equipped` - the tool was moved into a character;
- `Unequipped` - the tool was moved out of a character;
- `Activated` - the holder clicked while the tool was equipped.

## Notes

A `Part` named `Handle` inside the tool is moved to the character's hand while the tool is held, and its collisions are disabled.
