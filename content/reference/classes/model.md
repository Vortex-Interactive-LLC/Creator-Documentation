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

</details>

</ul>
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

## Images
<img src="../../../images/examples/modelCenterExample1.png" alt="Model w/ Move Tool" width="400"/>

## Notes

A `Model` exposes the generic instance surface, including hierarchy and attribute methods. Instances parented to a Model become its children: `FindFirstChild`, `GetChildren()`, `GetDescendants()`, and `WaitForChild` all find them. `GetPivot`, `PivotTo`, and `MoveTo` are available. `Position`, `PrimaryPart`, and `WorldPivot` are not readable from a script, and `GetPrimaryPartCFrame` and `SetPrimaryPartCFrame` are not available.

The live [Character](./character.md) Model is a special case. It exposes `ClassName`, `Name`, and `Position`, plus direct `Humanoid` and `HumanoidRootPart` members; `Parent` reads as `nil`. It provides the generic Instance methods, `MoveTo`, and `PivotTo`.

Characters can be turned by assigning `Character.Orientation` from a server Script. See [Character: Rotating a character](./character.md#rotating-a-character).

`Character:FindFirstChild("Humanoid")` and `Character:FindFirstChild("HumanoidRootPart")` return the same direct members. The standard R6/R15 body parts are not children of the character. Character attribute values replicate in both directions between a server Script and the owning LocalScript; see the [Attributes guide](../../guides/attributes.md).
