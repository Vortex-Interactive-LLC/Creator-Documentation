---
title: Model
description: A collection of Explorer items grouped into one object.
---

<!-- 
Model
Revision 1

Written by KingTasaz on August 28th, 2026
-->

## Summary
Models are a very simple way to group [`parts`](./part.md) together. Creating a model requires at least `2` selected parts, but the second part can be deleted afterward. Parts in a model are not truly connected; they are only grouped in the Explorer. Models currently have no purpose other than organization.

A model with no children is still shown in the explorer, but does not exist in the world and has no transform controls.

The basic transform tools (Move, Rotate) work more or less as expected when used on a model, except for scaling, which is currently not properly supported.

<details>
<summary><b>Properties</b></summary>
Properties of a Model, in the order they appear in Vortex Studio
<br><br>
<ul>

<details>
<summary><b>Properties</b></summary>

- [Name](#name): `string`
- [Position](#position): [`Vector3`](../datatypes/vector3.md)
- [PrimaryPart](#primarypart): [`BasePart`](./part.md) | `nil`
- [WorldPivot](#worldpivot): [`CFrame`](../datatypes/cframe.md)
- [Locked](#locked): `boolean`

</details>

</ul>
</details>

<details>
<summary><b>Methods</b></summary>

Methods of a `Model`.
<br><br>

- [MoveTo](#moveto): `nil`
- [TranslateBy](#translateby): `nil`
- [GetBoundingBox](#getboundingbox): [`CFrame`](../datatypes/cframe.md), [`Vector3`](../datatypes/vector3.md)
- [GetExtentsSize](#getextentssize): [`Vector3`](../datatypes/vector3.md)

</details>

## Properties


### Name
> `string` \
\
The name of the `model` and its label in the Explorer.

<br/>


### Position
> [`Vector3`](../datatypes/vector3.md) \
\
The position of the `model`, in world space. A model's position is automatically set to the mathematical average of the positions of all its children. (See [Images](#images))

<br/>


### PrimaryPart
> [`BasePart`](./part.md) | `nil` \
\
The part the model's pivot follows. When it is set, the pivot of the `model` is the pivot of that part. When it is `nil`, the pivot is [`WorldPivot`](#worldpivot).

<br/>


### WorldPivot
> [`CFrame`](../datatypes/cframe.md) \
\
The pivot of the `model` in world space, used when it has no [`PrimaryPart`](#primarypart). Setting it moves the pivot without moving any of the parts.

<br/>


### Locked
> `boolean` \
\
Defaults to `false`. Marks the model as locked in the Studio Explorer so it cannot be selected in the viewport.

<br/>

## Methods

### MoveTo()
> `nil` \
\
`Model:MoveTo(position: Vector3)` \
\
Moves the `model` so that its pivot is at `position`.

<br/>


### TranslateBy()
> `nil` \
\
`Model:TranslateBy(offset: Vector3)` \
\
Moves the `model` and every part in it by `offset`, keeping their rotation.

<br/>


### GetBoundingBox()
> [`CFrame`](../datatypes/cframe.md), [`Vector3`](../datatypes/vector3.md) \
\
`Model:GetBoundingBox()` \
\
Returns the center and the size of the smallest box that fits all the parts in the `model`, aligned to the model's pivot. A model with no parts returns its pivot and a zero size.

<br/>


### GetExtentsSize()
> [`Vector3`](../datatypes/vector3.md) \
\
`Model:GetExtentsSize()` \
\
Returns the size of the bounding box from [`GetBoundingBox`](#getboundingbox).

<br/>

## Images
<img src="../../../images/examples/modelCenterExample1.png" alt="Model w/ Move Tool" width="400"/>

## Notes

A `Model` exposes the generic instance surface, including hierarchy and attribute methods. Instances parented to a Model become its children: `FindFirstChild`, `GetChildren()`, `GetDescendants()`, and `WaitForChild` all find them. `GetPivot`, `PivotTo`, `MoveTo`, `TranslateBy`, `GetBoundingBox`, and `GetExtentsSize` are available. `PrimaryPart` and `WorldPivot` are readable and writable from a script. `GetPrimaryPartCFrame` and `SetPrimaryPartCFrame` are not available.

The live [Character](./character.md) Model is a special case. It exposes `ClassName`, `Name`, and `Position`, plus direct `Humanoid` and `HumanoidRootPart` members; `Parent` reads as `nil`. It provides the generic Instance methods, `MoveTo`, and `PivotTo`.

A server Script can turn a live character by assigning `Character.Orientation` or using `PivotTo`. See [Character: Rotating a character](./character.md#rotating-a-character).

`Character:FindFirstChild("Humanoid")` and `Character:FindFirstChild("HumanoidRootPart")` return the same direct members. The standard R6/R15 body parts are not children of the character. Attributes a server Script sets on a character reach the owning LocalScript, but not the other way round; see the [Attributes guide](../../guides/attributes.md).
