---
title: Model
description: A collection of explorer items, grouped into one object
---

<!-- 
Model
Revision 1

Written by KingTasaz on August 28th, 2026
Updated by LocalScriptMaker on October 25th, 2026
-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `Model`.
<br><br>

* [Position](#position): `Vector3`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `Model`.
<br><br>

* [GetPivot](#getpivot): `CFrame`
* [PivotTo](#PivotTo)
* [MoveTo](#moveto)

</details>

## Overview
Models are a very simple way to group [`parts`](./part.md) together.
Creating a model requires at least 2 parts selected, but otherwise the second part can be deleted. Parts in a model are not truly connected, but only grouped in the explorer.

A model with no children is still shown in the explorer, but does not exist in the world and has no transform controls.

The basic transform tools (Move, Rotate) work more or less as expected when used on a model, except for scaling which currently is not properly supported.

## Properties

### Position

> `Model.Position: Vector3`
>
> Determines position in 3D space.

## Methods

### GetPivot

> `Model:GetPivot(): CFrame`
>
> Returns `CFrame` of the Model's center.

### PivotTo

> `Model:PivotTo(targetCFrame: CFrame)`
>
> Transforms the `Model` at the specified `CFrame`. Returns nothing.

#### Parameters

- `targetCFrame: CFrame` — The `CFrame` into which the `Model` transforms

### MoveTo

> `Model:MoveTo(targetPosition: Vector3)`
>
> Moves the `Model` to the given position.

#### Parameters

- `targetPosition: Vector3` — The `Vector3` the `Model` is moved to.

## Testing Notes

In Vortex Studio 0.8.1, a detached `Model` exposes the generic instance
surface, including hierarchy and attribute methods, but has no readable `PrimaryPart`, or `WorldPivot` property. This is identical in
both `Script` and `LocalScript`.

`GetPrimaryPartCFrame`, and `SetPrimaryPartCFrame` are
also unavailable (`nil`) in both contexts. Assigning `Model.PrimaryPart` is
rejected as a non-settable property.

In 0.8.1, the live [Character](../guides/character.md) Model is a special case. In both a `LocalScript` and
a confirmed server `Script`, it exposes `ClassName`, `Name`, and `Position`, plus
direct `Humanoid` and `HumanoidRootPart` members; `Parent` reads as `nil`.
It exposes the tested generic Instance method surface and a connectable
`Changed` signal, but its tested hierarchy/lifecycle signals are unavailable.
Like a detached Model, its pivot and primary-part APIs remain unavailable.

The live Character Model is also the verified write-only visual rotation
target: `character.Orientation = Vector3.new(0, 90, 0)` visibly turns the
character in a server Script while the field remains `nil` on readback. See
[Character: Write-only visual rotation](./character.md#write-only-visual-rotation).

`Character:FindFirstChild("Humanoid")` and
`Character:FindFirstChild("HumanoidRootPart")` return the same direct members. Character attribute values replicate in both directions between a
server `Script` and the owning `LocalScript`; see the
[Attributes guide](../../guides/attributes.md).
