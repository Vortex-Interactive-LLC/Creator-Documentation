---
title: Humanoids & Characters
description: Read and change a player's health, speed and position from a script.
---
Each player's body in the world is a [`Character`](../reference/classes/character.md), and its [`Humanoid`](../reference/classes/humanoid.md) holds health and movement settings. Get the character from `player.Character`, or from the `CharacterAdded` signal. See [Players Joining & Leaving](player-events.md).

```luau
-- Script
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local humanoid = character:FindFirstChild("Humanoid")
        local root = character:FindFirstChild("HumanoidRootPart")
        print(player.Name, humanoid.Health, root.Position)
    end)
end)
```

`Humanoid` and `HumanoidRootPart` are the only children you can rely on. The usual body part names are not children of the character.

## Health

A new character has `Health` and `MaxHealth` of `100`. In a server `Script` you can assign both, and setting `Health` to `0` kills the character, which then respawns with full health.

```luau
humanoid.Health = 50
humanoid:TakeDamage(20)  -- 30 left
humanoid.Health = 0      -- dies
```

`TakeDamage` can only be called from a server `Script`. A freshly spawned character has a `ForceField` for about three seconds, and `TakeDamage` does nothing while it is present. Assigning to `Health` directly is not blocked.

```luau
humanoid.Died:Connect(function()
    print("died")
end)

humanoid.HealthChanged:Connect(function(health)
    print("health is now", health)
end)
```

`humanoid:IsDead()` returns whether the character is dead.

## Movement settings

| Property | Default | Notes |
| --- | --- | --- |
| `WalkSpeed` | `16` | Can be assigned from a server `Script`. |
| `JumpPower` | `50` | Can be assigned from a server `Script`. |
| `JumpHeight` | about `6.4` | |
| `HipHeight` | `0` | |
| `AutoRotate` | `true` | |
| `Sit` | `false` | |

```luau
humanoid.WalkSpeed = 30
humanoid.JumpPower = 80
```

`StateChanged`, `Jumping`, `FreeFalling`, `Running` and `Seated` are available as signals.

## Moving a character

Move a character by setting its position, either through the model or the root part.

```luau
character:MoveTo(Vector3.new(0, 10, 0))
character:PivotTo(CFrame.new(0, 10, 0))
root.CFrame = CFrame.new(0, 10, 0)
```

To turn a character, set `Character.Orientation` or `root.Orientation`, or pass a rotated `CFrame` to `PivotTo`. The root part's `Size` is read-only, because the server controls the character's physical state. See [`HumanoidRootPart`](../reference/classes/humanoid-root-part.md).

## Holding tools

`humanoid:EquipTool(tool)` and `humanoid:UnequipTools()` move tools between the backpack and the character. See [Tools & the Backpack](tools-and-backpack.md).
