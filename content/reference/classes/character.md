---
title: Character
description: The runtime Model projection associated with a Player.
---

A Character is the live [`Model`](./model.md) exposed by a player's [`Player.Character`](./player.md) field. It is not a separately constructible Vortex class. Obtain it from the local player in a LocalScript or from a Player returned by `Players:GetPlayers()` in a server Script.

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

## Write-only visual rotation

`Character.Orientation` is the confirmed server-side method for turning the visible Character. Assigning `Vector3.new(0, 90, 0)` visibly quarter-turns the character even though `Character.Orientation` is `nil` before the assignment and remains `nil` after it. Treat it as a write-only visual command rather than as readable transform state:

```luau
character.Orientation = Vector3.new(0, 90, 0)
```

After the turn, `Character.Orientation` still reads `nil`. The exposed visual hierarchy supplies `Position` values only; it does not expose the resulting yaw for readback.

This differs from the public [`HumanoidRootPart`](./humanoid-root-part.md), which rejects the write.

## Visual Scene projection

`Character:GetChildren()` returns an unnamed generic `Instance`. After a short loading delay, that wrapper can expose a separate `Scene` property containing the rendered armature, body meshes, limbs, and avatar-specific attachments. It is a transient renderer projection rather than part of the normal Character hierarchy.

Once that visual Scene is available, the observed direct-member path is:

```luau
local wrapper = character:GetChildren()[1]
local scene = wrapper.Scene
local armature = scene["Armature.001"]
local visualRoot = armature.HumanoidRootPart
local torso = visualRoot.Torso
local rightLeg = torso["Right Leg"]
local body = scene.Body

local VisualTorso = body["R7Body.Material.001"]
local VisualHead = body["R7Body.Material.002"]
local VisualRightArm = body["R7Body.Material.004"]
local VisualLeftArm = body["R7Body.Material.005"]
local VisualRightLeg = body["R7Body.Material.007"]
local VisualLeftLeg = body["R7Body.Material.008"]
```

Names containing dots or spaces require bracket syntax. `HumanoidRootPart`, `Torso`, and `Head` are direct members on their respective visual nodes. This visual root is not the restricted public `character.HumanoidRootPart` Part projection.

The Scene can be replaced while the Character itself remains available. A replacement destroys old visual instances, so stored limb or accessory references cannot be reparented into the new Scene. Resolve the current visual Scene whenever it is needed. See [Model: Transient Character visual Scene](./model.md#transient-character-visual-scene) for the full observed tree, visual-node surface, and attachment details.

The tested visual `HumanoidRootPart` and `Torso` also ignore an `Orientation` write without producing an error: the value remains `nil` on readback. They cannot be used to control rotation.

The tested `R7Body.Material` does not have any working properties (Position, size, etc.), the only working property found during testing is :Destroy().

## Lifecycle

`Player.CharacterAdded` and `Player.CharacterRemoving` fire when a character spawns or is removed. When a character's Humanoid dies, the player respawns with a new character. A newly spawned character has a `ForceField` child for a few seconds.
