---
title: Part
description: A primitive rectangular prism
---

<!-- 
Part
Revision 2

Written by KingTasaz on August 28th, 2026
-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `IntValue`.
<br><br>

* [Value](#value): `number`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `IntValue`.
<br><br>

* [Changed](#changed): `Connection`

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
> 


### Orientation
> [`Vector3`](../datatypes/vector3.md) \
\
The rotation of the `Part` in degrees along each axis.

<br/>


### Parent
> [`Instance`](./instance.md) | `nil` \
\
The containing `Instance` of the `Part`, or `nil` when it has no parent.

<br/>


### Position
> [`Vector3`](../datatypes/vector3.md) \
\
The position of the `Part`, in World-space.

<br/>


### Rotation
> [`Vector3`](../datatypes/vector3.md) \
\
The rotation of the `Part` along each axis.

<br/>


### Size
> [`Vector3`](../datatypes/vector3.md) \
\
The size of the `Part` in each dimension (width, height, depth).

<br/>


### Transparency
> `Float` \
\
Sets the `transparency` of the part from `0` (opaque) to `1` (invisible).
When drawing shadows, all parts are treated as opaque regardless of their `transparency`. Unless it is set to `1`, where the part does not render at all.

<br/>


### Truss
> `Boolean` \
\
If a `part` is a truss part, then the `Player` is able to climb the part by walking up to it. It is recommened to keep truss parts anchored, as they otherwise produce unpredictable effects.

<br/>

## Methods

### Clone()
> `Part` \
\
Creates and returns a copy of the `Part`.

<br/>


### Destroy()
> `nil` \
\
Destroys the `Part`.

<br/>


### FindFirstChild()
> [`Instance`](./instance.md) | `nil` \
\
`part:FindFirstChild(name: string)` \
\
Returns the first direct child with the supplied `name`, or `nil` when none is
found.

<br/>


### FindFirstChildOfClass()
> [`Instance`](./instance.md) | `nil` \
\
`part:FindFirstChildOfClass(className: string)` \
\
Returns the first direct child whose class matches `className`, or `nil` when
none is found.

<br/>


### GetAttribute()
> `Variant` | `nil` \
\
`part:GetAttribute(name: string)` \
\
Returns the value stored under the supplied attribute `name`.

<br/>


### GetAttributeChangedSignal()
> [`Signal`](../datatypes/signal.md) \
\
`part:GetAttributeChangedSignal(name: string)` \
\
Returns an event associated with changes to the supplied attribute `name`.

<br/>


### GetAttributes()
> `{ [string]: Variant }` \
\
Returns a table containing the `Part` attributes.

<br/>


### GetChildren()
> `{ Instance }` \
\
Returns the direct children of the `Part`.

<br/>


### GetDescendants()
> `{ Instance }` \
\
Returns the descendants of the `Part`.

<br/>


### GetPropertyChangedSignal()
> [`Signal`](../datatypes/signal.md) \
\
`part:GetPropertyChangedSignal(property: string)` \
\
Returns an event associated with changes to the supplied property.

<br/>


### IsA()
> `Boolean` \
\
`part:IsA(className: string)` \
\
Returns whether the `part` is an instance of `className` or one of its
ancestor classes.

<br/>


### SetAttribute()
> `nil` \
\
`part:SetAttribute(name: string, value: Variant | nil)` \
\
Sets the attribute `name` to `value`. Passing `nil` clears the attribute.

<br/>


### WaitForChild()
> [`Instance`](./instance.md) \
\
`part:WaitForChild(name: string)` \
\
Waits for and returns a direct child with the supplied `name`.

<br/>

## Events

### Changed
> [`Signal`](../datatypes/signal.md) \
\
An event associated with changes to the `part`.

<br/>


### Touched
> [`Signal`](../datatypes/signal.md) \
\
An event associated with physical contact with the `part`.

<br/>


### TouchEnded
> [`Signal`](../datatypes/signal.md) \
\
An event associated with the end of physical contact with the `part`.

<br/>

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later
releases.

> [!WARNING]
> After `child.Parent = part` succeeds, `child.Parent == part` is `false`.
> `WaitForChild(childName)` resolves the child, but `FindFirstChild`,
> `FindFirstChildOfClass`, `GetChildren`, and `GetDescendants` do not expose
> it.

`Changed`, `GetPropertyChangedSignal`, and `GetAttributeChangedSignal` expose
connectable events, but changing the corresponding property or attribute does
not deliver callbacks. `Touched` and `TouchEnded` are connectable; their event
delivery has not been established.

> [!NOTE]
> A server Script can read a player's
> [`Character.HumanoidRootPart`](./humanoid-root-part.md), but assigning its
> current `Position` or `Size` is rejected as client-side, server-authoritative
> character state. This restriction applies to the live character root part; it
> does not change the tested behavior of ordinary script-created Parts.
