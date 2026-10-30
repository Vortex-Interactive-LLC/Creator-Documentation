---
title: Humanoid
description: Represents the humanoid controller of a player's Character.
---

The current player's humanoid is available as `game:GetService("Players").LocalPlayer.Character.Humanoid` in a `LocalScript`. A server `Script` can also reach a visible player's character through `game:GetService("Players"):GetPlayers()[1].Character`. The character's root transform is exposed separately as a [`HumanoidRootPart`](./humanoid-root-part.md).

## Summary

<details>
<summary><b>Properties</b></summary>

Properties of the `Humanoid`.
<br><br>

* [ClassName](#classname): `string`
* [Name](#name): `string`
* [Health](#health): `Number`
* [MaxHealth](#maxhealth): `Number`

</details>

<details>
<summary><b>Methods</b></summary>

Methods of the `Humanoid`.
<br><br>

* [IsDead](#isdead): `Boolean`
* [GetState](#getstate): `Enum.HumanoidStateType`

</details>

<details>
<summary><b>Signals</b></summary>

Signals of the `Humanoid`.
<br><br>

* [Died](#died): [`Signal`](../datatypes/signal.md)
* [HealthChanged](#healthchanged): [`Signal`](../datatypes/signal.md)
* [StateChanged](#statechanged): [`Signal`](../datatypes/signal.md)
* [Jumping](#jumping): [`Signal`](../datatypes/signal.md)
* [FreeFalling](#freefalling): [`Signal`](../datatypes/signal.md)
* [Running](#running): [`Signal`](../datatypes/signal.md)

</details>

## Properties

### ClassName

> `string`
>
> The class name of the Humanoid, `"Humanoid"`.

<br/>

### Name

> `string`
>
> The name of the Humanoid.

<br/>

### Health

> `Number`
>
> The current health value.

<br/>

### MaxHealth

> `Number`
>
> The maximum health value.

<br/>

## Methods

### IsDead

> `Boolean`
>
> `humanoid:IsDead()`
>
> Returns whether the Humanoid is dead.

### GetState

> `Enum.HumanoidStateType`
>
> `humanoid:GetState()`
>
> Returns the Humanoid's current state. On a server `Script` this is `Running`, `Freefall`, `Climbing`, `Seated`, or `Dead`, taken from what the player's client reports.

## Signals

### Died

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.Died`
>
> Fires when the Humanoid dies.

<br/>

### HealthChanged

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.HealthChanged`
>
> Fires when the Humanoid's health changes.

### StateChanged

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.StateChanged`
>
> Fires when the Humanoid's state changes.

### Jumping

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.Jumping`
>
> Fires when the Humanoid is jumping.

### FreeFalling

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.FreeFalling`
>
> Fires when the Humanoid enters or leaves the freefall state.

### Running

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.Running`
>
> Fires when the Humanoid enters or leaves the running state.

#### Parameters

- `health`: `Number` — the updated health value.

## Notes

A character's Humanoid starts with `Health` and `MaxHealth` of `100`. In a server `Script`, both can be assigned, and assigning `Health = 0` kills the character. The character then respawns with full health. `Died` and `HealthChanged` fire when the Humanoid dies or its health changes.

`humanoid:TakeDamage(amount)` reduces `Health`. A newly spawned character has a `ForceField` for a few seconds, and damage is blocked while it is present.

`WalkSpeed`, `JumpPower`, `JumpHeight`, and `HipHeight` are numbers, and `AutoRotate` and `Sit` are booleans. `WalkSpeed` can be assigned from a server `Script`. `StateChanged`, `Jumping`, `FreeFalling`, `Running`, and `Seated` are available as signals.

A Humanoid does not provide the generic Instance methods (`IsA`, `FindFirstChild`, `GetAttribute`, `Destroy`, and so on). Methods such as `ChangeState`, `Move`, `MoveTo`, `LoadAnimation`, and `AddAccessory` are not available.
