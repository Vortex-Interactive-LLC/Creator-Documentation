---
title: Player
description: An instance holding information about a connected client.
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `Player`.
<br><br>

* [Character](#character): `Model`
* [UserId](#userid): `number`
* [DisplayName](#displayname): `string`
* [Character](#character): `Model`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `Player`.
<br><br>

* [GetMouse](#getmouse): `Mouse`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `Player`.
<br><br>

* [CharacterAdded](#characteradded): `Connection`
* [CharacterRemoving](#characterremoving): `Connection`

</details>

## Overview

Represents a connected client. The current client is available through the
[Players](./players.md) service as
`LocalPlayer`.

## Code Samples

```luau
-- LocalScript

local Players = game:GetService("Players")
local player = Players.LocalPlayer

print("Hello, " .. player.Name .. "!")
```

## Properties

### Character

> `Player.Character: Model`
>
> The player's default physical representation in the world.

### UserId

> `Player.UserId: number`
>
> A unique identifying integer assigned to all user accounts, in ascending order.

### DisplayName

> `Player.DisplayName: string`
>
> Player's username, equivalent to `Player.Name`.

## Methods

### GetMouse

> `GetMouse(): Mouse`
>
> Returns an instance of the `Mouse` class.

## Signals

### CharacterAdded

> `CharacterAdded(character: Model): Connection`
>
> Fires after the `Player` has joined the game and spawned in world

### CharacterRemoving

> `CharacterRemoving(character: Model): Connection`
>
> Fires after the `Player` has left the game

## Player transform projection fields

`Player.Position`, `Player.Rotation`, and `Player.CFrame` begin as `nil` but
accept and retain assigned `Vector3`/`CFrame` values in both a server `Script`
and a `LocalScript`. They do not update the public
`Character.HumanoidRootPart`: an explicit three-stud `Player.Position` write
left the root at its original position in both contexts, and a
`Player.Rotation` write likewise caused no translation.

`Position` and `Rotation` are also context-local. A 15-second server writer /
`LocalScript` observer run, followed by the contexts swapped, showed that each
writer retained its own values while the observer stayed `nil`. Do not use
these fields for character movement, replicated state, or a server-client
metadata channel.

`Player.Orientation` likewise accepts and retains a `Vector3`, but the
isolated transform sequence did not establish it as a visual rotation route.
Use [`Character.Orientation`](./character.md#write-only-visual-rotation)
instead when the goal is to turn the visible Character.

## Methods and signals

The 0.8.1 `Player` surface probe did not expose any of the tested standard Player
or Instance methods, nor any tested lifecycle, chat, hierarchy, or change
signals. This includes `GetChildren`, attributes, `GetMouse`, `Kick`, and
`LoadCharacter`.

A dedicated 15-second observer also found `Player.CharacterAdded` to be `nil`
in both a LocalScript and a server Script throughout its full window. The
delayed and replaced visual Character Scene therefore does not correspond to
an exposed `Player` character-lifecycle signal.

## Observed character projection

The following is the confirmed, directly accessible portion of a player's
runtime character projection in Vortex Studio 0.3.4:

```text
Player
└── Character (Model)
    ├── Humanoid
    └── HumanoidRootPart (Part projection)
```

[`Character`](../../guides/character.md), [`Humanoid`](../../guides/humanoid.md), and
[`HumanoidRootPart`](../../guides/humanoid-root-part.md) are direct readable members—not
a `Player:GetChildren()` result. `Character:FindFirstChild` resolves the same
Humanoid and root-part values. `Character:GetChildren()` instead returns one
unnamed generic `Instance`, so it is not a usable character-rig inventory.
The other tested standard R6 body-part and `Animate` names were absent
from the public Character projection. The anonymous child can later expose a
separate, transient visual `Scene` containing the rendered rig and
avatar-specific attachments; see [Model: Transient Character visual
Scene](./model.md#transient-character-visual-scene).

## Vortex Studio 0.8.1 notes

`Players.LocalPlayer` is available in a `LocalScript` and `nil` in a normal
server `Script`. In both contexts, the Player surface probe found only
`ClassName`, `Name`, and `Character` as non-`nil` fields. A server Script can obtain this `Player`
through `Players:GetPlayers()[1]`.
