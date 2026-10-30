---
title: Character
description: The runtime Model projection associated with a Player.
---

A Character is the live [`Model`](./model.md) exposed by a player's [`Player.Character`](./player.md#character) field. It is not a separately constructible Vortex class. Obtain it from the local player in a LocalScript or from a Player returned by `Players:GetPlayers()` in a server Script.

```luau
-- LocalScript
local character = game:GetService("Players").LocalPlayer.Character
```

```luau
-- Script
local player = game:GetService("Players"):GetPlayers()[1]
local character = player and player.Character
```

## Confirmed public projection

The live Character reports `ClassName == "Model"`. Its public fields are `ClassName`, `Name`, `Position`, [`Humanoid`](./humanoid.md), and [`HumanoidRootPart`](./humanoid-root-part.md). `Parent` reads as `nil`.

The generic Instance methods are available, including `GetChildren`, `GetDescendants`, `FindFirstChild`, `FindFirstChildOfClass`, `WaitForChild`, `IsA`, `Clone`, `Destroy`, and the attribute methods. `MoveTo` and `PivotTo` move the character. `PrimaryPart` is not available.

`Character:FindFirstChild("Humanoid")` and `Character:FindFirstChild("HumanoidRootPart")` resolve the same direct values as the public fields. The standard R6/R15 limb names are not children of the character.

## Rotating a character

A server `Script` can turn a character by assigning `Character.Orientation` (or `HumanoidRootPart.Orientation`) or by passing a rotated `CFrame` to `Character:PivotTo(cframe)`. Only the rotation around the Y axis is used, and the character keeps that facing until the player moves and turns them. `Character:MoveTo(position)` changes the position only.

## Lifecycle

`Player.CharacterAdded` and `Player.CharacterRemoving` fire when a character spawns or is removed. When a character's Humanoid dies, the player respawns with a new character. A newly spawned character has a `ForceField` child for a few seconds.
