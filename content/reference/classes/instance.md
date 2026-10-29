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
> Vortex Studio 0.3.4 does not expose a uniform set of Instance methods on 
> every engine-backed value. The members below describe ordinary Instance-like
> objects. Use the concrete class reference and the availability matrix on this
> page before calling a method.

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
| [`Workspace`](./workspace.md) | Yes | No | Yes | Yes | No | No | No | No |
| [`ReplicatedStorage`](./replicated-storage.md) | Yes | No | Yes | Yes | No | No | No | No |
| [`Players`](./players.md) | No | No | No | No | No | No | No | No |
| [`Player`](./player.md) | No | No | No | No | No | No | No | No |
| [`Humanoid`](./humanoid.md) | No | No | No | No | No | No | No | No |

The `Players` service can still provide its class-specific `GetPlayers()` method, and a `Humanoid` can provide `IsDead()`, even though the generic methods above are absent.

These observations were made in Vortex Studio 0.3.4 and may change in later versions.
