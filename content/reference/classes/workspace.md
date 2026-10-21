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
- [Raycast](#raycast): [`RaycastResult`](../datatypes/raycast-result.md) | `nil`
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
Returns the first direct child with the supplied `name`, or `nil` when none is
found.

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
- `raycastParams`: An optional object used to specify hit eligibility during the raycast operation.

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

The hierarchy observations below were revalidated in Vortex Studio 0.3.4 and
may differ in later releases.

0.3.4. A temporary `Part` can be parented to `Workspace`,
and `WaitForChild` resolves it. `FindFirstChild` returns `nil` and
`GetChildren` omits it.

For existing authored children, repeated `GetChildren()` calls can return new
Lua wrapper tables for the same underlying Instance. Do not use a returned
wrapper as a persistent table key between frames; use a unique authored name or
another stable identifier instead.
