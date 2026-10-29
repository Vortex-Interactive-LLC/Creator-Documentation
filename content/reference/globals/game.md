---
title: Game
description: The root instance of a game.
---

<!-- 
Game
Revision 2

Written by Kindtracker on August 29th, 2026
Edited by MtcLuna05 on August 30th, 2026
-->

> [!NOTE]
> There will be more things (methods, constructors, properties, etc.) in the future.

`game` is the root instance and provides access to services.

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `game`.
<br><br>

* [Workspace](#workspace): [`Workspace`](/content/reference/classes/workspace.md)
* [Players](#players): [`Players`](/content/reference/classes/players.md)

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `game`.
<br><br>

* [GetService(serviceName: `string`)](#getservice): `Instance`

</details>

<details>
<summary><b>Callbacks</b></summary>
Callbacks of `game`.
<br><br>

* [OnClose](#onclose): `Function` | `nil`

</details>

<details>
<summary><b>Services</b></summary>
Services of `game`.
<br><br>

* [Workspace](../classes/workspace.md)
* [Players](../classes/players.md)
* [ReplicatedStorage](../classes/replicated-storage.md)
* [StarterPlayerScripts](../classes/starter-player-scripts.md)
* [ServerScriptService](../classes/server-script-service.md)
* [Lighting](../classes/lighting.md) (editor-facing; not exposed by `game:GetService` in 0.3.4)
* [Debris](../classes/debris.md)
* [RunService](./runservice.md)
* [TweenService](../classes/tween-service.md)
* [UserInputService](./user-input-service.md)

</details>

## Properties

### Workspace

> [`Workspace`](../classes/workspace.md)
>
> The root `Workspace` service.

<br/>

### Players

> [`Players`](../classes/players.md)
>
> A direct alias for the Players service. In Vortex Studio 0.3.4 it is a distinct proxy table from `game:GetService("Players")`.

<br/>

## Methods

### GetService()

> `Instance`
>
> `game:GetService(serviceName: string)`
>
> Returns the service with the specified name.

#### Parameters

- `serviceName`: `string` — the name of the service to retrieve.

<br/>

## Callbacks

### OnClose

> `Function` | `nil`
>
> An optional callback that can be assigned before the game closes.

<br/>

## Services

### Workspace

> `Instance`
>
> The Workspace is the root object that holds anything that is currently in the world. [Workspace](../classes/workspace.md)

<br/>

### Players

> `Instance`
>
> The service that contains the currently connected player objects. [Players](../classes/players.md)

<br/>

### ReplicatedStorage

> `Instance`
>
> A container for instances loaded by both the server and the client. [ReplicatedStorage](../classes/replicated-storage.md)

<br/>

### StarterPlayerScripts

> `Instance`
>
> Stub. [StarterPlayerScripts](../classes/starter-player-scripts.md)

<br/>

### ServerScriptService

> `Instance`
>
> ServerScriptService contains [Scripts](../classes/script.md) that run when the server starts. [ServerScriptService](../classes/server-script-service.md)

<br/>

### Lighting

> Unavailable in the tested runtime
>
> `game:GetService("Lighting")` rejects this service in both Script and LocalScript in Vortex Studio 0.3.4. [Lighting](../classes/lighting.md)

<br/>

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later releases.

`game.Workspace` and `game:GetService("Workspace")` both report `ClassName` and `Name` as `Workspace`. `game.OnClose` starts as `nil`; assigning a function succeeds, but callback delivery has not been established.
