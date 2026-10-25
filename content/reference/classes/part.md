---
title: Part
description: A primitive rectangular prism
---

<!-- 
Part
Revision 2

Written by KingTasaz on August 28th, 2026
Updated by LocalScriptMaker on October 25th, 2026
-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `Part`.
<br><br>

* [Anchored](#anchored): `boolean`
* [CanCollide](#cancollide): `boolean`
* [CanQuery](#canquery): `boolean`
* [CanTouch](#cantouch): `boolean`
* [Color](#color): `Color3`
* [Transparency](#transparency): `number`
* [Material](#material): `Enum.Material`
* [CastShadow](#castshadow): `boolean`
* [Velocity](#velocity): `Vector3`
* [AngularVelocity](#angularvelocity): `Vector3`
* [Position](#position): `Vector3`
* [Orientation](#orientation): `Vector3`
* [Rotation](#rotation): `Vector3`
* [CFrame](#cframe): `CFrame`
* [Size](#size): `Vector3`
* [Shape](#shape): `Enum.PartType`
* [CenterOfMass](#centerofmass): `Vector3`
* [Mass](#mass): `number`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `Part`.
<br><br>

* [Touched](#touched): `Connection`
* [TouchEnded](#touchended): `Connection`

</details>

## Overview

A `Part` is a `BasePart` that comes in different primitive shapes.

## Properties

### Anchored

> `Part.Anchored: boolean`
>
> Determines when a part is subject to physics.

### CanCollide

> `Part.CanCollide: boolean`
>
> Determines when a part has a collision.

### CanQuery

> `Part.CanQuery: boolean`
>
> Determines whether the part will be ignored when a ray hits it. `CanQuery` always `true` if part is collidable, else can be set manually.

### CanTouch

> `Part.CanTouch: boolean`
>
> Determines when a part supports triggering the `Touched` and `TouchEnded` signals.

### Color

> `Part.Color: Color3`
>
> Visual color of a part's surface.

### Transparency

> `Part.Transparency: number`
>
> Determines how much a part can be seen through.

### Material

> `Part.Material: Enum.Material`
>
> Appearance of a part.

### CastShadow

> `Part.CastShadow: boolean`
>
> Determines whether the part will cast a shadow.

### Velocity

> `Part.Velocity: Vector3`
>
> Describes how its `Part.Position` is presently changing. The unit of this property is studs per second

### AngularVelocity

> `Part.AngularVelocity: Vector3`
>
> Describes how its `Part.Orientation` is presently changing. The unit of this property is studs per second

### Position

> `Part.Position: Vector3`
>
> Determines position in 3D space.

### Orientation

> `Part.Orientation: Vector3`
>
> Rotation of the part in the world. **Applied in Y → X → Z axis.**

### Rotation

> `Part.Rotation: Vector3`
>
> Rotation of the part in the world. **Applied in X → Y → Z axis.**

### CFrame

> `Part.CFrame: CFrame`
>
> Represents both a 3D `Position` and `Orientation` of the `Part`.

### Size

> `Part.Size: Vector3`
>
> Determines part's visual dimensions like length, height, width.

### Shape

> `Part.Shape: Enum.PartType`
>
> Sets the overall shape of the object.

### CenterOfMass

> `Part.CenterOfMass: Vector3`
>
> Describes the local `Position` of a part's center of mass, relative to its `CFrame`.

### Mass

> `Part.Mass: number`
>
> Determines how "heavy" a `Part` is, based on its `Size`.

## Signals

### Touched

> `Touched(otherPart: BasePart): Connection`
>
> Fires when a `Part` touches another `Part`.

#### Parameters

- `otherPart: BasePart` — the `Part` that came in contact with the given `Part`.

### TouchEnded

> `TouchEnded(otherPart: BasePart): Connection`
>
> Fires when a `Part` stops touching another `Part`.

#### Parameters

- `otherPart: BasePart` — the `Part` that stopped touching this `Part`.

## Testing Notes

These observations are from Vortex Studio 0.8.1 and may differ in later
releases.

`Changed`, `GetPropertyChangedSignal`, and `GetAttributeChangedSignal` expose
connectable events. `Touched` and `TouchEnded` are connectable; their event
delivery has not been established.
