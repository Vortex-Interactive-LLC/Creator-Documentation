---
title: Player
description: An instance holding information about a connected client.
---

## Summary

Represents a connected client. The current client is available as `LocalPlayer` through the
[Players](./players.md)

### Example

```luau
-- LocalScript

local Players = game:GetService("Players")
local player = Players.LocalPlayer

print("Hello, " .. player.Name .. "!")
```

## Properties

- `Name` - the player's name;
- `ClassName` - `"Player"` for the current client projection;
- `Character` - the current [`Character`](./character.md) `Model`, when available.
- `Position`, `Rotation`, and `CFrame` - initially `nil`, writable
  Player-local projection fields in the tested runtime. They are not aliases
  for the public character root's physical transform.
- `Orientation` - an initially `nil`, writable
  [`Vector3`](../datatypes/vector3.md) projection field. Its retained value
  is not the verified method for visibly turning the Character.

## Player transform projection fields

`Player.Position`, `Player.Rotation`, and `Player.CFrame` begin as `nil` but
accept and retain assigned `Vector3`/`CFrame` values in both a server Script
and a LocalScript. They do not update the public
`Character.HumanoidRootPart`: an explicit three-stud `Player.Position` write
left the root at its original position in both contexts, and a
`Player.Rotation` write likewise caused no translation.

`Position` and `Rotation` are also context-local. A 15-second server-writer/
LocalScript-observer test, followed by another test with the contexts swapped,
showed that each writer retained its own values while the observer remained `nil`. 
Do not use these fields for character movement, replicated state, 
or a server-client metadata channel.

`Player.Orientation` likewise accepts and retains a `Vector3`, but the
isolated transform sequence did not establish it as a method for visual rotation.
Use [`Character.Orientation`](./character.md#write-only-visual-rotation)
instead when the goal is to turn the visible Character.

## Methods and signals

The 0.3.4 Player surface probe did not expose any of the tested standard Player
or Instance methods or any of the tested lifecycle, chat, hierarchy, or change
signals. This includes `GetChildren`, attributes, `GetMouse`, `Kick`, and
`LoadCharacter`.

A dedicated 15-second observation also found `Player.CharacterAdded` to be `nil`
in both a LocalScript and a server Script throughout the entire observation period. 
The delayed and replaced visual Character Scene therefore does not correspond to
any exposed Player character-lifecycle signal.
## Observed character projection

The following is the confirmed, directly accessible portion of a player's
runtime character projection in Vortex Studio 0.3.4:

```text
Player
└── Character (Model)
    ├── Humanoid
    └── HumanoidRootPart (Part projection)
```

[`Character`](./character.md), [`Humanoid`](./humanoid.md), and
[`HumanoidRootPart`](./humanoid-root-part.md) are directly readable members
a `Player:GetChildren()` result. `Character:FindFirstChild` resolves the same
Humanoid and root-part values. `Character:GetChildren()` instead returns one
unnamed generic `Instance`, so it cannot be used as a reliable inventory of the character rig.
The other tested standard R6/R15 body-part and `Animate` names were absent
from the public Character projection. The anonymous child can later expose a
separate, transient visual `Scene` containing the rendered rig and
avatar-specific attachments; see [Model: Transient Character visual
Scene](./model.md#transient-character-visual-scene).

## Vortex Studio 0.3.4 notes

`Players.LocalPlayer` is available in a `LocalScript` and `nil` in a normal
server `Script`. In both contexts, the Player surface probe found only
`ClassName`, `Name`, and `Character` as non-`nil` fields. `Parent` reads as
`nil` for the observed LocalPlayer. A server Script can obtain this Player
through `Players:GetPlayers()`, but it cannot identify the Player from a 
RemoteEvent's numeric sender ID.

The client `LocalPlayer` and the server-visible Player both lack the Instance
attribute methods. Player attributes therefore cannot be used as a
server-to-client metadata channel in the tested runtime.
