---
title: Instance
description: Shared conventions for engine-backed objects in Vortex.
---

<!-- 
Instance
Revision 1

Written by Kindtracker on August 28th, 2026
Updated by LocalScriptMaker on October 25th, 2026
-->

> [!IMPORTANT]
> Vortex Studio 0.8.1 does not expose one uniform Instance method set on every
> engine-backed value. The members below describe ordinary Instance-like
> objects. Use the concrete class reference and the availability matrix on this
> page before calling a method.

## Summary

<details>
<summary><b>Properties</b></summary>
Common properties of an `Instance`-like object.
<br><br>

* [Name](#name): `string`
* [ClassName](#classname): `string`
* [Parent](#parent): `Instance | nil`

</details>

<details>
<summary><b>Signals</b></summary>
Common signals of an `Instance`-like object.

* [Changed](#changed): `Connection`
  
<br><br>

* [Name](#name): `string`

</details>

## Properties

### Name

> `Instance.Name: string`
>
> The name of the `Instance`.

### ClassName

> `Instance.ClassName: string`
>
> The name of the `Instance` class.

### Parent

> `Instance.Parent: Instance | nil`
>
> The instance's hierarchical parent, or `nil` when it has no parent.

## Signals

### Changed

> `Changed(property: string)`
>
> Fires after a property of the object changes. Returns property.

#### Parameters

- `property`: `string` — changed property.

### Code Samples

```luau
local function onChanged(property)
    print("The new property's value is",object[property])
end

object.Changed:Connect(onChanged)
```

See this [reference](../instance) to find more instance methods.

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

A `Players` service can still provide its class-specific `GetPlayers()` method, and a `Humanoid` can provide `IsDead()`, even though the generic methods above are absent.

These observations were made in Vortex Studio 0.8.1 and may change in later versions.
