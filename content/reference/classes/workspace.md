---
title: Workspace
description: Service that holds and renders every 3D player-interactable instance.
---

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of a `Workspace`.
<br><br>

- [GetServerTimeNow](#getservertimenow): `number`
- [Raycast](#raycast): `RaycastResult?`
- [Spherecast](#spherecast): `RaycastResult?`
- [Blockcast](#blockcast): `RaycastResult?`

</details>

## Overview

Service `Workspace` houses 3D objects which are rendered to the 3D world.

## Methods

### GetServerTimeNow

> `workspace:GetServerTimeNow(): number`
>
> Returns the server's Unix time in seconds.

### Raycast

> `workspace:Raycast(origin: Vector3, direction: Vector3, raycastParams: table?): RaycastResult?`
>
> Casts a ray from the specified origin in the specified direction. The function returns a [RaycastResult](../datatypes/raycast-result.md) if an eligible object intersects the ray, or `nil` if no object is hit.

#### Parameters

- `origin`: `Vector3` — The origin point of the ray.
- `direction`: `Vector3` — The directional vector of the ray.
- `raycastParams`: `table` — An optional table used to specify hit eligibility during the raycast operation.

### Spherecast

> `workspace:Spherecast(origin: Vector3, radius: number, direction: Vector3, raycastParams: table?): RaycastResult?`
>
> Casts a spherical-shape ray with a specified radius from the specified origin in the specified direction. The function returns a [RaycastResult](../datatypes/raycast-result.md) if an eligible object intersects the ray, or `nil` if no object is hit.

#### Parameters

- `origin`: `Vector3` — The origin point of the ray.
- `radius`: `number` — The radius of the cast spherical shape in studs. The maximum radius is 256 studs.
- `direction`: `Vector3` — The directional vector of the ray.
- `raycastParams`: `table?` — An optional table used to specify hit eligibility during the raycast operation.

### Blockcast

> `workspace:Blockcast(origin: CFrame, size: Vector3, direction: Vector3, raycastParams: table?): RaycastResult?`
>
> Casts a block-shape ray with a specified size from the specified origin in the specified direction. The function returns a [RaycastResult](../datatypes/raycast-result.md) if an eligible object intersects the ray, or `nil` if no object is hit.

#### Parameters

- `origin`: `CFrame` — The origin point of the ray.
- `size`: `number` — The size of the cast block shape in studs. The maximum size is 512 studs.
- `direction`: `Vector3` — The directional vector of the ray.
- `raycastParams`: `table?` — An optional table used to specify hit eligibility during the raycast operation.

## Testing Notes

The hierarchy observations below were revalidated in Vortex Studio 0.8.1 and
may differ in later releases.

0.8.1. A temporary `Part` can be parented to `Workspace`,
and `WaitForChild` resolves it. `FindFirstChild` returns `nil` and
`GetChildren` omits it.

For existing authored children, repeated `GetChildren()` calls can return fresh
Lua wrapper tables for the same underlying Instance. Do not use a returned
wrapper as a persistent table key across frames; use a unique authored name or
another stable identifier instead.
