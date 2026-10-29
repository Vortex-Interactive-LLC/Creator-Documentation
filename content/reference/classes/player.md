---
title: Player
description: An instance holding information about a connected client.
---

## Summary

Represents a connected client. The current client is available as `LocalPlayer` through the [Players](./players.md) service.

### Example

```luau
-- LocalScript

local Players = game:GetService("Players")
local player = Players.LocalPlayer

print("Hello, " .. player.Name .. "!")
```

## Properties

- `Name` - the player's name;
- `DisplayName` - the player's display name;
- `UserId` - the player's numeric user id;
- `ClassName` - `"Player"`;
- `Parent` - the [`Players`](./players.md) service;
- `Character` - the current [`Character`](./character.md) `Model`, when available;
- `Backpack` - the player's `Backpack`.

## Methods and signals

A `Player` is an Instance. It provides the generic Instance methods, including `GetChildren`, `FindFirstChild`, `IsA`, `Clone`, `Destroy`, and the attribute methods (see the [Attributes guide](../../guides/attributes.md)). `Player:GetMouse()` can only be called on the `LocalPlayer` from a `LocalScript`.

`CharacterAdded` and `CharacterRemoving` fire when the player's character spawns or is removed. `Kick` and `LoadCharacter` are not available.

## Character

[`Character`](./character.md), [`Humanoid`](./humanoid.md), and [`HumanoidRootPart`](./humanoid-root-part.md) are directly readable members of the character:

```text
Player
└── Character (Model)
    ├── Humanoid
    └── HumanoidRootPart (Part)
```

`Character:FindFirstChild("Humanoid")` and `Character:FindFirstChild("HumanoidRootPart")` resolve the same values. The standard R6/R15 body-part names and `Animate` are not children of the character.

## Notes

`Players.LocalPlayer` is available in a `LocalScript` and `nil` in a normal server `Script`. A server Script gets players from `Players:GetPlayers()` or from the first argument of a `RemoteEvent`'s `OnServerEvent`.
