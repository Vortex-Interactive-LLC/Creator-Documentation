---
title: Humanoid
description: Represents the humanoid controller of a player's Character.
---

The current player's humanoid is available as
`game:GetService("Players").LocalPlayer.Character.Humanoid` in a `LocalScript`.
In Vortex Studio 0.3.4, a server `Script` can also reach a visible player's
character through `game:GetService("Players"):GetPlayers()[1].Character`.
The character's root transform is exposed separately as a
[`HumanoidRootPart`](./humanoid-root-part.md).

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
> Returns the Humanoid's current state.

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

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later
releases.

The observed Character's Humanoid was a specialized table with `ClassName` and
`Name` both reporting `"Humanoid"`, and `Health` and `MaxHealth` both
reporting `100`. `IsDead()` was exposed and returned `false`. `Died` and
`HealthChanged` exposed signals that support `Signal:Connect`.

Assigning `Health` or `MaxHealth` is rejected in both a `LocalScript` and a
confirmed server `Script` (`RunService:IsServer()` returned `true`). The error still
states that the value is read-only in a LocalScript and that character state is server-authoritative,
so its wording does not match the observed server behavior. Server code can now
enumerate a `Player`, read its `Character`, and obtain this `Humanoid`, but that
projection does not currently grant authority to write to Health.

`WalkSpeed`, `JumpPower`, `JumpHeight`, and `UseJumpPower` read as `nil` on the
tested server-visible Humanoid projection, so their write behavior remains
unknown. `Died` and `HealthChanged` are exposed Signal references; their
delivery remains unconfirmed.

TThe confirmed server-side API exposes only `IsDead()`. The Roblox-style
`TakeDamage` method, along with state/movement control, animation, and accessory methods
all read as `nil`. Of the tested Roblox-style signals, only `Died` and
`HealthChanged` are connectable; `Jumping`, `FreeFalling`, `Running`,
`StateChanged`, `MoveToFinished`, `PlatformStanding`, `Ragdoll`, and `Seated`
all read as `nil`.

The specialized Humanoid has an opaque `__index` and `__newindex` metatable;
`IsA` was not exposed on the value itself.
