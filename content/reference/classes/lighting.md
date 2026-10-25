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

In Vortex Studio 0.8.1, `game:GetService("Lighting")` and also like `game.Lighting` fails with
`"Lighting" is not a valid service` in both `Script` and `LocalScript`. The
editor-facing Lighting controls documented below therefore do not currently
have a confirmed runtime scripting surface.

There are two main controls under Lighting's properties:
- `Ambient` is the general lighting that every object receives regardless of its position or rotation.
- `Sun` is the light placed on object faces that are in direct view of the sun. If shadows are enabled, then parts of a face can be blocked from the sun.
<br><br>

<details>
<summary><b>Properties</b></summary>
Properties of Lighting, in the order they appear on Vortex Studio.
<br><br>
<ul>
<details>
<summary><b>Appearance</b></summary>

- [Ambient Color](#ambient-color): [`Color3`](../datatypes/color3.md)
- [Brightness](#brightness): `number`
- [Sun Color](#sun-color): [`Color3`](../datatypes/color3.md)
- [Sun Brightness](#sun-brightness): `number`
- [Sun Shadows](#sun-shadows): `boolean`

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
Will also affect the part's [`Material`]() color.

<br/>

### Brightness
> `number` \
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
Determines the angle at which sunlight hits objects, and as such the dimensions of shadows.

<br/>


### Size
> [`Vector3`](../datatypes/vector3.md) \
\
This value is `read-only` has `no effect`.

<br/>

### Sun Brightness
> `number` \
\
Determines how bright the `sun` lighting is.

<br/>

### Sun Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the color of sunlight that hits objects.
Will blend with the ambient coloring.

<br/>

### Sun Shadows
> `boolean` \
\
Toggles shadows globally (from the sun).
Currently, there are no other types of lights that create shadows, so this is a toggle button for every shadow in your game.

<br/>
