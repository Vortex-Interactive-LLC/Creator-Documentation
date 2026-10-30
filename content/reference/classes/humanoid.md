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
* [WalkSpeed](#walkspeed): `Number`
* [JumpPower](#jumppower): `Number`
* [JumpHeight](#jumpheight): `Number`
* [HipHeight](#hipheight): `Number`
* [AutoRotate](#autorotate): `Boolean`
* [Sit](#sit): `Boolean`
* [SeatPart](#seatpart): [`Seat`](./seat.md) | `nil` (read-only)

</details>

<details>
<summary><b>Methods</b></summary>

Methods of the `Humanoid`.
<br><br>

* [IsDead](#isdead): `Boolean`
* [GetState](#getstate): `Enum.HumanoidStateType`
* [TakeDamage](#takedamage): `nil`
* [EquipTool](#equiptool): `nil`
* [UnequipTools](#unequiptools): `nil`

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
* [Seated](#seated): [`Signal`](../datatypes/signal.md)

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

### WalkSpeed

> `Number`
>
> How fast the character walks, in studs per second. Defaults to `16`. Can be assigned from a server `Script`. Negative values are treated as `0`.

<br/>

### JumpPower

> `Number`
>
> The upward speed of a jump. Defaults to `50`. Can be assigned from a server `Script`.

<br/>

### JumpHeight

> `Number`
>
> How high a jump reaches, in studs. Defaults to about `6.4`. It is derived from `JumpPower`, so setting one changes the other.

<br/>

### HipHeight

> `Number`
>
> The height of the character's root part above the ground. Defaults to `0`.

<br/>

### AutoRotate

> `Boolean`
>
> When `true`, the character turns to face the direction it is moving. Defaults to `true`.

<br/>

### Sit

> `Boolean`
>
> `true` while the character is sitting in a [`Seat`](./seat.md). Setting it to `false` removes the character from its seat. Setting it to `true` does not seat the character.

<br/>

### SeatPart

> [`Seat`](./seat.md) | `nil`
>
> The seat the character is sitting in, or `nil` when it is not seated. This property is read-only.

<br/>

## Methods

### IsDead

> `Boolean`
>
> `humanoid:IsDead()`
>
> Returns whether the Humanoid is dead.

### TakeDamage

> `nil`
>
> `humanoid:TakeDamage(amount: Number)`
>
> Reduces `Health` by `amount`. Server `Script` only. Does nothing while the character has a [`ForceField`](./force-field.md).

### EquipTool

> `nil`
>
> `humanoid:EquipTool(tool: Tool)`
>
> Moves `tool` into the character so that it is held. Server `Script` only. Raises an error if `tool` is not a [`Tool`](./tool.md), and does nothing if the character is dead.

### UnequipTools

> `nil`
>
> `humanoid:UnequipTools()`
>
> Moves every held tool back into the player's [`Backpack`](./backpack.md). Server `Script` only.

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

### Seated

> [`Signal`](../datatypes/signal.md)
>
> `humanoid.Seated`
>
> Fires when the character sits down or gets up.

#### Parameters

- `active`: `Boolean` — `true` when the character sits down, `false` when it gets up.
- `seatPart`: [`Seat`](./seat.md) — the seat involved.

## Notes

A character's Humanoid starts with `Health` and `MaxHealth` of `100`. In a server `Script`, both can be assigned, and assigning `Health = 0` kills the character. The character then respawns with full health. `Died` and `HealthChanged` fire when the Humanoid dies or its health changes.

`humanoid:TakeDamage(amount)` reduces `Health`. A newly spawned character has a `ForceField` for a few seconds, and damage is blocked while it is present.

A Humanoid does not provide the generic Instance methods (`IsA`, `FindFirstChild`, `GetAttribute`, `Destroy`, and so on). Methods such as `ChangeState`, `Move`, `MoveTo`, `LoadAnimation`, and `AddAccessory` are not available.
