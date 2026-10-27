---
title: SpotLight
description: A conical light emitting from a single point 
---

<!-- 
SpotLight
Revision 1

Written by KingTasaz on August 28th, 2026
-->

## Summary
A `spotlight` must be the child of a [`Part`](./part.md), and takes the position of its parent as its own.

There is currently no on/off switch for lights, but setting either the color, brightness, angle, or range to 0 will have the desired effect.

Under the `properties` tab, SpotLights visibly have Position, Rotation, and Size attributes. Position and Rotation are `read-only` and size has `no effect`. It is possible these values were left in by accident.

## Runtime scripting limitation

In Vortex Studio 0.3.4, `Instance.new("SpotLight")` succeeds in both Script
and LocalScript, but produces a non-functional class shell. It exposes generic
Instance methods and a connectable `Changed` signal, while the tested
light-specific fields initially read as `nil`.

`Brightness`, `Range`, `Angle`, `Enabled`, and `Shadows` are not settable.
`Color` accepts and retains a `Color3` value, but assigning `Parent` to a
temporary Part succeeds without establishing parentage or adding a child.
Consequently, there is no confirmed script route for configuring or attaching
a rendered SpotLight in the current runtime.

<details>
<summary><b>Properties</b></summary>
Properties of a SpotLight, in the order they appear on Vortex Studio.
<br><br>
<ul>
<details>
<summary><b>Appearance</b></summary>

- [Color](#color): [`Color3`](../datatypes/color3.md)
- [Brightness](#brightness): `Float`
- [Range](#range): `Float`
- [Angle](#angle): `Float`
- [Face](#face): [`Enum.Face`](../datatypes/enumitem.md)

</details>

<details>
<summary><b>Transform</b></summary>

- [Name](#name): `string`

</details>

</ul>
</details>

## Properties

### Angle
> `number` \
\
The angle of the emission cone.
Smaller angles can produce sharper cutoffs, and wider angles create a softer fall off.

<br/>

### Brightness
> `number` \
\
The emission brightness of the light. Does not affect range.

<br/>

### Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the color of the emitted light.
Darker colors have the same effect as turning off the light.

<br/>


### Face
> [`Enum.Face`](../datatypes/enumitem.md) \
\
Controls which face of the parent [`Part`](./part.md) that the light is emitted from.

<br/>


### Name
> `string` \
\
The name of the `spotlight`, and its label in the explorer.

<br/>


### Range
> `number` \
\
The maximum (linear) range that the light can reach.
This controls the drop-off of the brightness over time, but does not increase the brightness.

<br/>
