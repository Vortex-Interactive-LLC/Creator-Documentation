---
title: Instance
description: Shared conventions for engine-backed objects in Vortex.
---

<!-- 
Instance
Revision 1

Written by Kindtracker on August 28th, 2026
-->

> [!IMPORTANT]
> Most instances share the members below. A few engine-backed values do not: `Humanoid` exposes none of the generic Instance methods, `HumanoidRootPart` exposes only `IsA`, and `Players` exposes only `FindFirstChild` and `GetChildren`. Check the availability matrix on this page and the concrete class reference before calling a method.

## Summary

<details>
<summary><b>Properties</b></summary>
Common properties of an `Instance`-like object.
<br><br>

* [Name](#name): `string`
* [Parent](#parent): `Instance | nil`

</details>

<details>
<summary><b>Methods</b></summary>
Common methods of an `Instance`-like object.
<br><br>

* [Clone()](#clone): `Instance`
* [Destroy()](#destroy): `nil`
* [GetChildren()](#getchildren): `{ Instance }`

</details>

## Properties

### Name

> `string` 
>
> The name of the `Instance`.

<br/>

### Parent

> `Instance | nil`
>
> The instance's hierarchical parent, or `nil` when it has no parent.

<br/>

## Methods

### Clone()

> `Instance` 
>
> Creates a copy of the `Instance` and returns the copy.

<br/>

### Destroy()

> `nil` 
>
> Destroys the `Instance` and its children.

<br/>

### GetChildren()

> `{ Instance }` 
>
> Returns children of the `Instance`.

<br/>

## Vortex Studio Method Availability

The following matrix records whether each member is exposed as a function on the live object.

| Runtime object | `FindFirstChild` | `FindFirstChildOfClass` | `WaitForChild` | `GetChildren` | `GetDescendants` | `Clone` | `Destroy` | `IsA` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [`Part`](./part.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Script`](./script.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Character`](./character.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Workspace`](./workspace.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`ReplicatedStorage`](./replicated-storage.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`ServerScriptService`](./server-script-service.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Player`](./player.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Players`](./players.md) | Yes | No | No | Yes | No | No | No | No |
| [`Humanoid`](./humanoid.md) | No | No | No | No | No | No | No | No |
| [`HumanoidRootPart`](./humanoid-root-part.md) | No | No | No | No | No | No | No | Yes |

`Players` also provides its class-specific methods such as `GetPlayers()`, and a `Humanoid` provides `IsDead()`, `GetState()`, and `TakeDamage()`, even though the generic methods above are absent.
