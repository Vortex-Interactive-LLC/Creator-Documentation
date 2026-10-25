---
title: Humanoid
description: Represents the humanoid controller in a Player Character.
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `Humanoid`.
<br><br>

* [Health](#health): `number`
* [MaxHealth](#maxhealth): `number`
* [WalkSpeed](#walkspeed): `number`
* [JumpPower](#jumppower): `number`
* [JumpHeight](#jumpheight): `number`
* [AutoRotate](#autorotate): `boolean`
* [HipHeight](#hipheight): `number`
* [MoveDirection](#movedirection): `Vector3`
* [Sit](#sit): `boolean`
* [SeatPart](#seatpart): `BasePart`

</details>

<details>
<summary><b>Methods</b></summary>
Signals of `Humanoid`.
<br><br>

* [IsDead](#isdead): `boolean`
* [GetState](#getstate): `Enum.HumanoidStateType`
* [TakeDamage](#takedamage)

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `Humanoid`.
<br><br>

* [Died](#died): `Connection`
* [HealthChanged](#healthchanged): `Connection`
* [StateChanged](#statechanged): `Connection`
* [Jumping](#jumping): `Connection`
* [Running](#running): `Connection`
* [FreeFalling](#freefalling): `Connection`
* [Seated](#seated): `Connection`

</details>

## Overview

`Humanoid` provides character functionality.

The current player's humanoid is available in both contexts; `Script` and `LocalScript`.

```luau
-- Script

local player = game:GetService('Players'):GetPlayers()[1]
local character = player and player.Character or player and player.CharacterAdded:Wait()
local humanoid:Humanoid = character:WaitForChild('Humanoid')
```

```luau
-- LocalScript

local player = game:GetService('Players').LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid:Humanoid = character:WaitForChild('Humanoid')
```

## Properties

### Health

> `Humanoid.Health: number`
>
> The current health value. If the `Humanoid` is dead, this property is continually set to 0.

### MaxHealth

> `Humanoid.MaxHealth: number`
>
> The maximum health value.

### WalkSpeed

> `Humanoid.WalkSpeed: number`
>
> Determines how quickly the `Humanoid` is able to walk, in studs per second.

### JumpPower

> `Humanoid.JumpPower: number`
>
> Determines how much upwards force is applied to the `Humanoid` when jumping.

### JumpHeight

> `Humanoid.JumpPower: number`
>
> Determines how much studs `Humanoid` can jump.

### AutoRotate

> `Humanoid.AutoRotate: boolean`
>
> Determines whether or not the `Humanoid` will automatically rotate to face in the direction they are moving.

### HipHeight

> `Humanoid.HipHeight: number`
>
> Determines the distance in studs off the ground the `HumanoidRootPart` should be.

### MoveDirection

> `Humanoid.MoveDirection: Vector3`
>
> Normalized Vector3 that describes the direction a `Humanoid` is walking in.

### Sit

> `Humanoid.Sit: boolean`
>
> Describes whether the `Humanoid` is currently sitting.

### SeatPart

> `Humanoid.SeatPart: BasePart`
>
> A part that a `Humanoid` is currently sitting in.

## Methods

### IsDead

> `IsDead(): boolean`
>
> Returns whether the `Humanoid` is dead.

### GetState

> `GetState(): Enum.HumanoidStateType`
>
> Returns the Humanoid's current state.

### TakeDamage

> `TakeDamage(amount: number)`
>
> Lowers the `Health` property by the given amount if it is not protected by a `ForceField`. Returns nothing.

#### Parameters

- `amount`: `number` — damage amount

## Signals

### Died

> `Died()`
>
> Fires when when `Health` property reaches 0. Returns nothing.

### HealthChanged

> `HealthChanged(health: number)`
>
> Signals when the `Health` property changes. Returns new health amount.

#### Parameters

- `health`: `number` — current `Health` value

### StateChanged

> `StateChanged(old: Enum.HumanoidStateType, new: Enum.HumanoidStateType)`
>
> Signals when the `Humanoid` state changes. Returns `Humanoid` states.

#### Parameters

- `old`: `Enum.HumanoidStateType` — The `Humanoid` previous state type.
- `new`: `Enum.HumanoidStateType` — The `Humanoid` current state type.

### Jumping

> `Jumping(active: boolean)`
>
> Signals when the `Humanoid` is jumping. Returns when `Humanoid` entering or leaving `Enum.HumanoidStateType.Jumping`

#### Parameters

- `active`: `boolean` — `Jumping` state `boolean`

### Running

> `Running(speed: number)`
>
> Signals when the `WalkSpeed` property of `Humanoid` changes. Returns current `WalkSpeed` value 

#### Parameters

- `speed`: `number` — Current `WalkSpeed` value 

### FreeFalling

> `FreeFalling(active: boolean)`
>
> Signals when the `Humanoid` is falling. Returns when `Humanoid` entering or leaving `Enum.HumanoidStateType.Freefall`

#### Parameters

- `active`: `number` — `Freefall` state boolean

### Seated

> `Seated(active: boolean, seat: BasePart)`
>
> Fires when a `Humanoid` sits in or gets up from a `Seat`

#### Parameters

- `active`: `boolean` — `Seated` state `boolean`
- `seat`: `BasePart` — current `Seat` or `nil`

## Testing Notes

These observations are from Vortex Studio 0.8.1 and may differ in later
releases.

The observed character Humanoid was a specialized table with `ClassName` and
`Name` both reporting `"Humanoid"`, and `Health` and `MaxHealth` both
reporting `100`. `IsDead()` was exposed and returned `false`. `Died` and
`HealthChanged` exposed `Signal:Connect`.

`UseJumpPower` read as `nil` on the tested server-visible Humanoid projection, so their write behavior remains
unknown. `Died` and `HealthChanged` are exposed Signal references.

The confirmed server method surface contains `IsDead()` only. The Roblox-style
methods animation, and accessory methods all read as `nil`. Of the tested Roblox-style signals, only `Died` and
`HealthChanged` are connectable; `MoveToFinished`, `PlatformStanding`, `Ragdoll` all read as `nil`.

The specialized Humanoid has an opaque `__index` and `__newindex` metatable;

`ClassName` of `Connection` is `RBXScriptSignal`
