---
title: Workspace
description: A service that holds and renders every 3D instance that players can interact with.
---

<!-- 
Workspace
Revision 1.2

Written by Kindtracker on September 19, 2026
-->

## Summary

The `workspace` global is this service. Instances may not exist yet while the game is loading, so use `WaitForChild` or check for `nil` before using something you look up.

<details>
<summary><b>Properties</b></summary>
Properties of a Workspace, in the order they appear in Vortex Studio
<br><br>

- [ClassName](#classname): `string`
- [Name](#name): `string`
</details>

<details>
<summary><b>Methods</b></summary>

Methods of `Workspace`.
<br><br>

- [FindFirstChild](#findfirstchild): [`Instance`](./instance.md) | `nil`
- [GetChildren](#getchildren): `{ Instance }`
- [GetServerTimeNow](#getservertimenow): `number`
- [Blockcast](#blockcast): [`RaycastResult`](../datatypes/raycast-result.md) | `nil`
- [Raycast](#raycast): [`RaycastResult`](../datatypes/raycast-result.md) | `nil`
- [Spherecast](#spherecast): [`RaycastResult`](../datatypes/raycast-result.md) | `nil`
- [WaitForChild](#waitforchild): [`Instance`](./instance.md)

</details>

## Properties

### ClassName
> `string` \
\
The runtime class name of the service.

<br/>


### Name
> `string` \
\
The service name shown by the runtime.

<br/>

## Methods

### FindFirstChild()
> [`Instance`](./instance.md) | `nil` \
\
`workspace:FindFirstChild(name: string)` \
\
Returns the first direct child with the supplied `name`, or `nil` when none is found.

#### Parameters

- `name`: `string` — the name of the child to find.

<br/>


### GetChildren()
> `{ Instance }` \
\
Returns the direct children of `Workspace`.

<br/>


### Raycast()
> `RaycastResult | nil` 
\
`Workspace:Raycast(origin: Vector3, direction: Vector3, raycastParams: RaycastParams | nil)`
\
Casts a ray from the specified origin in the specified direction. The function returns a [RaycastResult](../datatypes/raycast-result.md) if an eligible object intersects the ray, or `nil` if no object is hit.

#### Parameters

- `origin`: `Vector3` — The origin point of the ray.
- `direction`: `Vector3` — The directional vector of the ray.
- `raycastParams`: An optional [`RaycastParams`](../datatypes/raycast-params.md) table used to specify hit eligibility during the raycast operation.

<br/>


### Spherecast()
> `RaycastResult | nil` \
\
`Workspace:Spherecast(origin: Vector3, radius: number, direction: Vector3, raycastParams: RaycastParams | nil)` \
\
Sweeps a sphere of the given `radius` from `origin` along `direction`. Returns a [RaycastResult](../datatypes/raycast-result.md) for the first eligible object it touches, or `nil` if nothing is hit. Available in a `LocalScript` only: calling it from a server `Script` raises an error.

#### Parameters

- `origin`: `Vector3` — the starting position of the sphere's center.
- `radius`: `number` — the radius of the sphere.
- `direction`: `Vector3` — the direction and distance of the sweep.
- `raycastParams`: An optional [`RaycastParams`](../datatypes/raycast-params.md) table used to specify hit eligibility.

<br/>


### Blockcast()
> `RaycastResult | nil` \
\
`Workspace:Blockcast(cframe: CFrame, size: Vector3, direction: Vector3, raycastParams: RaycastParams | nil)` \
\
Sweeps a box of the given `size`, positioned and rotated by `cframe`, along `direction`. Returns a [RaycastResult](../datatypes/raycast-result.md) for the first eligible object it touches, or `nil` if nothing is hit. Available in a `LocalScript` only: calling it from a server `Script` raises an error.

#### Parameters

- `cframe`: [`CFrame`](../datatypes/cframe.md) — the starting position and rotation of the box.
- `size`: `Vector3` — the dimensions of the box.
- `direction`: `Vector3` — the direction and distance of the sweep.
- `raycastParams`: An optional [`RaycastParams`](../datatypes/raycast-params.md) table used to specify hit eligibility.

<br/>


### GetServerTimeNow()
> `number` \
\
`Workspace:GetServerTimeNow()` \
\
Returns the current server time as a Unix timestamp in seconds.

<br/>


### WaitForChild()
> [`Instance`](./instance.md) \
\
`workspace:WaitForChild(name: string)` \
\
Waits for and returns a direct child with the supplied `name`.

#### Parameters

- `name`: `string` — the name of the child to wait for.


<br/>

## Testing Notes

A `Part` or other instance parented to `Workspace` is found by `FindFirstChild`, `WaitForChild`, and `GetChildren`.
