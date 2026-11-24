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

`game:GetService("Lighting")` fails with `"Lighting" is not a valid service` in both Script and LocalScript. The editor-facing Lighting controls documented below therefore do not currently have a confirmed runtime scripting surface.

There are two main controls in Lighting's properties:
- `Ambient` is the general lighting that every object receives regardless of its position or rotation.
- `Sun` is the light that illuminates object faces that are directly exposed to the sun. If shadows are enabled, then parts of a face can be blocked from sunlight.
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
Determines the color of the ambient light that every object receives, regardless of its position or rotation.

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
Determines how bright the sunlight is.

<br/>

### Sun Color
> [`Color3`](../datatypes/color3.md) \
\
Determines the color of sunlight that hits objects. It will blend with the ambient color.

<br/>

### Sun Shadows
> `Boolean` \
\
Toggles shadows from the sun globally. Currently, there are no other types of lights that create shadows, so this setting controls all shadows in the game.

<br/>

## Time, sky and fog

### ClockTime
> `Float` \
\
The time of day in hours, from `0` to `24`. Values outside the range wrap around, so `25` is `1`. It moves the sun across the sky and changes the colour of the sky. Defaults to `14`.

<br/>

### GeographicLatitude
> `Float` \
\
The latitude in degrees the sun's path is calculated for. It changes how high the sun rises and where it sets. Defaults to `41.733`.

<br/>

### FogColor
> [`Color3`](../datatypes/color3.md) \
\
The colour of the fog. Until it is set, it follows the colour of the sky at the horizon as `ClockTime` changes. Once it is set, it keeps the colour that was set.

<br/>

### FogStart
> `Float` \
\
The distance from the camera, in studs, where fog starts to appear. Defaults to `0`.

<br/>

### FogEnd
> `Float` \
\
The distance from the camera, in studs, where the fog is at full strength. Defaults to `100000`, which leaves the fog effectively off.

<br/>
