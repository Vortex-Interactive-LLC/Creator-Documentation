---
title: Tools & the Backpack
description: Give players items to hold, and react when they equip and use them.
---
A [`Tool`](../reference/classes/tool.md) is an item a player can hold. Each player has a [`Backpack`](../reference/classes/backpack.md) that stores the tools they are not currently holding.

## Giving tools to players

Put tools in `StarterPack`. Every player receives a copy in their backpack when they join, and gets fresh copies each time they respawn.

```luau
-- Script
local tool = Instance.new("Tool")
tool.Name = "Sword"
tool.Parent = game:GetService("StarterPack")
```

To give a tool to one player, parent a copy to their backpack:

```luau
local copy = tool:Clone()
copy.Parent = player.Backpack
```

Inside a `PlayerAdded` handler `player.Backpack` is still `nil`. Use `player:WaitForChild("Backpack")` there.

Anything in the player's backpack when they die is removed, and the backpack is refilled from `StarterPack` on respawn.

## Equipping

A tool is held when its parent is the player's character. Players equip from the backpack, and a script can do the same:

```luau
local humanoid = player.Character.Humanoid
humanoid:EquipTool(tool)
humanoid:UnequipTools()
```

Only one tool is held at a time. Equipping another moves the first one back to the backpack. `EquipTool` and `UnequipTools` can only be called from a server `Script`.

## Events

```luau
tool.Equipped:Connect(function()
    print("equipped")
end)

tool.Unequipped:Connect(function()
    print("put away")
end)

tool.Activated:Connect(function()
    print("used")
end)
```

`Activated` fires when the player who holds the tool clicks. It does not fire for a tool that is not equipped or when the holder is dead.

## Properties

`CanBeDropped` and `RequiresHandle` default to `true`. `ToolTip` is text and empty by default, and `TextureId` is a number that defaults to `0`. `Grip` and `GripPos` control how the tool is held. A part named `Handle` inside the tool is moved to the character's hand while it is held, and collisions are turned off for it.
