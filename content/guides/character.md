---
title: Character
description: The runtime Model projection associated with a Player.
---

# Summary

A Character is the live [`Model`](../reference/classes/model.md) exposed by a player's
`Player.Character` field. It is not a separately constructible
Vortex class. Obtain it from the local player in a LocalScript or from a Player
returned by `Players:GetPlayers()` in a server Script.

```luau
-- LocalScript
local player = game:GetService('Players').LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
```

```luau
-- Script
local player = game:GetService('Players'):GetPlayers()[1]
local character = player and player.Character or player and player.CharacterAdded:Wait()
```

<details>
<summary><b>Properties</b></summary>
Properties of `Character`.
<br><br>

* [Velocity](#velocity): `Vector3`
* [AngularVelocity](#angularvelocity): `Vector3`

</details>

## Properties

### Velocity

> `Character.Velocity: Vector3`
>
> Describes how its `Character.Position` is presently changing. The unit of this property is studs per second

### AngularVelocity

> `Character.AngularVelocity: Vector3`
>
> Describes how its `Character.Orientation` is presently changing. The unit of this property is studs per second

***

Other supported properties, methods and signals see in the [`Model`](../reference/classes/model.md) reference
