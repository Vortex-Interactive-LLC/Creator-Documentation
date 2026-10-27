---
title: PointLight
description: A spherical light emitting from a single point 
---

<!-- 
PointLight
Revision 1

Written by KingTasaz on August 28th, 2026
-->

## Summary
A `pointlight` must be the child of a [`part`](../classes/part.md), and takes the position of its parent as its own.

There is currently no on/off switch for lights, but setting either the color, brightness, or range to 0 will have the desired effect.

## Runtime scripting limitation

In Vortex Studio 0.3.4, `Instance.new("PointLight")` succeeds in both Script
and LocalScript, but produces a non-functional class shell. It exposes generic
Instance methods and a connectable `Changed` signal, while the tested
light-specific fields initially read as `nil`.

`Brightness`, `Range`, `Enabled`, and `Shadows` are not settable. `Color`
accepts and retains a `Color3` value, but assigning `Parent` to a temporary
Part succeeds without establishing parentage or adding a child. Consequently,
there is no confirmed script route for configuring or attaching a rendered
PointLight in the current runtime.

<details>
<summary><b>Properties</b></summary>
Properties of a Pointlight, in the order they appear on Vortex Studio.
<br><br>
<ul>
<details>
<summary><b>Appearance</b></summary>

- [Color](#color): [`Color3`](../datatypes/color3.md)
- [Brightness](#brightness): `Float`
- [Range](#range): `Float`

</details>

<details>
<summary><b>Transform</b></summary>

- [Name](#name): `string`

</details>

</ul>
</details>

## Properties

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


### Name
> `string` \
\
The name of the `pointlight`, and its label in the explorer.

<br/>


### Range
> `number` \
\
The maximum (spherical) range that the light can reach.
This controls the drop-off of the brightness over time, but does not increase the brightness.

<br/>
