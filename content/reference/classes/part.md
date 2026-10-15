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
Properties of a Part, in the order they appear in Vortex Studio.
<br><br>
<ul>
<details>
<summary><b>Appearance</b></summary>

- [Color](#color): [`Color3`](../datatypes/color3.md)
- [Transparency](#transparency): `Float`
- [Material](#material): [`Enum.Material`](../globals/enum.md) <!-- not sure if this should link to enumitem.md or enum.md <pretty sure it's enum.md> -->
- [Cast Shadow](#cast-shadow): `Boolean`

</details>

<details>
<summary><b>Behaviour</b></summary>

- [Anchored](#anchored): `Boolean`
- [CanCollide](#cancollide): `Boolean`
- [ClassName](#classname): `string`
- [Parent](#parent): [`Instance`](./instance.md) | `nil`
- [Truss](#truss): `Boolean`

</details>

<details>
<summary><b>Transform</b></summary>

- [CFrame](#cframe): [`CFrame`](../datatypes/cframe.md)
- [Name](#name): `string`
- [Position](#position): [`Vector3`](../datatypes/vector3.md)
- [Rotation](#rotation): [`Vector3`](../datatypes/vector3.md)
- [Size](#size): [`Vector3`](../datatypes/vector3.md)
- [Orientation](#orientation): [`Vector3`](../datatypes/vector3.md)

</details>

</ul>
</details>

<details>
<summary><b>Methods</b></summary>
<br>

- [Clone](#clone): `Part`
- [Destroy](#destroy): `nil`
- [FindFirstChild](#findfirstchild): [`Instance`](./instance.md) | `nil`
- [FindFirstChildOfClass](#findfirstchildofclass): [`Instance`](./instance.md) | `nil`
- [GetAttribute](#getattribute): `Variant` | `nil`
- [GetAttributeChangedSignal](#getattributechangedsignal): [`Signal`](../datatypes/signal.md)
- [GetAttributes](#getattributes): `{ [string]: Variant }`
- [GetChildren](#getchildren): `{ Instance }`
- [GetDescendants](#getdescendants): `{ Instance }`
- [GetPropertyChangedSignal](#getpropertychangedsignal): [`Signal`](../datatypes/signal.md)
- [IsA](#isa): `Boolean`
- [SetAttribute](#setattribute): `nil`
- [WaitForChild](#waitforchild): [`Instance`](./instance.md)

</details>

<details>
<summary><b>Events</b></summary>
<br>

- [Changed](#changed): [`Signal`](../datatypes/signal.md)
- [Touched](#touched): [`Signal`](../datatypes/signal.md)
- [TouchEnded](#touchended): [`Signal`](../datatypes/signal.md)
</details>

## Properties

### Anchored
> `Boolean` \
\
When `true`, the given part will be unable to move via interactions with the environment. \
When `false`, the part will experience gravity and forces from other parts.

<br/>


### CanCollide
> `Boolean` \
\
Determines whether the `Part` has physics collisions enabled or can phase through other parts. \
\
**Note:** A `Part` cannot be unanchored while collision is disabled.

<br/>


### CFrame
> [`CFrame`](../datatypes/cframe.md) \
\
Sets the position and rotation of the `Part` as a single transform.

<br/>


### ClassName
> `string` \
\
The runtime class name of the `Part`.

<br/>


### Cast Shadow
> `Boolean` \
\
Controls whether or not the `Part` will cast a shadow.
This can be used to improve performance for parts whose shadows cannot be seen, or for glass parts that would not realistically cast a shadow.

<br/>


### Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the visible color of the `Part`.
It will also affect the part's [`Material`]() color.

<br/>


### Material
> [`Enum.Material`](../datatypes/enumitem.md) \
\
Determines which `Material` type to apply when rendering the `Part`.
Currently, this only has a visual effect.

<br/>


### Name
> `string` \
\
The name of the `Part` and its label in the Explorer.

<br/>


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
The position of the `Part`, in world space.

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
When drawing shadows, all parts are treated as opaque regardless of their `transparency`, unless it is set to `1`, , in which case the part does not render at all.

<br/>


### Truss
> `Boolean` \
\
If a `part` is a truss part, then the `Player` can climb the part by walking up to it. It is recommended to keep truss parts anchored, as they can otherwise produce unpredictable effects.

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
connectable events, but changing the corresponding property or attribute does not trigger 
callbacks. `Touched` and `TouchEnded` are connectable; their event
delivery has not been established.

> [!NOTE]
> A server Script can read a player's
> [`Character.HumanoidRootPart`](./humanoid-root-part.md), but assigning its
> current `Position` or `Size` is rejected as client-side, server-authoritative
> character state. This restriction applies to the live character root part; it
> does not change the tested behavior of ordinary script-created Parts.
