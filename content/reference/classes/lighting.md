---
title: Lighting
description: Lighting is the game service that controls basic rendering and atmospherics
---

<!-- 
Lighting
Revision 1

Written by KingTasaz on August 28th, 2026
-->

## Summary
> [!NOTE]
> `Lighting` is a service and cannot be `created` or `destroyed`.

## Runtime availability

In Vortex Studio 0.3.4, `game:GetService("Lighting")` fails with
`"Lighting" is not a valid service` in both Script and LocalScript. The
editor-facing Lighting controls documented below therefore do not currently
have a confirmed runtime scripting surface.

There are two main controls in Lighting's properties:
- `Ambient` is the general lighting that every object receives regardless of its position or rotation.
- `Sun` is the light that illuminates object faces directly exposed to itself. If shadows are enabled, then parts of a face can be blocked from sunlight.
<br><br>

<details>
<summary><b>Properties</b></summary>
Properties of Lighting, in the order they appear in Vortex Studio.
<br><br>
<ul>
<details>
<summary><b>Appearance</b></summary>

- [Ambient Color](#ambient-color): [`Color3`](../datatypes/color3.md)
- [Brightness](#brightness): `Float`
- [Sun Color](#sun-color): [`Color3`](../datatypes/color3.md)
- [Sun Brightness](#sun-brightness): `Float`
- [Sun Shadows](#sun-shadows): `Boolean`

</details>

<details>
<summary><b>Transform</b></summary>

- [Position](#position): [`Vector3`](../datatypes/vector3.md)
- [Rotation](#rotation): [`Vector3`](../datatypes/vector3.md)
- [Size](#size): [`Vector3`](../datatypes/vector3.md)

</details>

</ul>
</details>


## Properties

### Ambient Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the visible color of the `Part`.
It will also affect the Part's [`Material`]() color.

<br/>

### Brightness
> `Float` \
\
Determines how bright the `ambient` lighting is.

<br/>


### Position
> [`Vector3`](../datatypes/vector3.md) \
\
This value has `no effect`.

<br/>


### Rotation
> [`Vector3`](../datatypes/vector3.md) \
\
Determines the angle at which sunlight hits objects and, as such, the dimensions of shadows.
<br/>


### Size
> [`Vector3`](../datatypes/vector3.md) \
\
This value is `read-only` and has `no effect`.

<br/>

### Sun Brightness
> `Float` \
\
Determines the brightness value of the `sun`.

<br/>

### Sun Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the color of sunlight that hits objects.
It will blend with the ambient color.

<br/>

### Sun Shadows
> `Boolean` \
\
Toggles shadows from the sun globally.
Currently, there are no other types of lights that create shadows, so this setting controls all shadows in the game.

<br/>
