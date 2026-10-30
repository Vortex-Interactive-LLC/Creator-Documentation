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
* [BindToClose(callback: `Function`)](#bindtoclose)

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
* [StarterGui](../classes/starter-gui.md)
* [StarterPack](../classes/starter-pack.md)
* [DataStoreService](../classes/data-store-service.md) (server only)
* [MarketplaceService](../classes/marketplace-service.md) (server only)
* [Lighting](../classes/lighting.md) (editor-facing; not a valid service for `game:GetService`)
* [Debris](../classes/debris.md)
* [RunService](./runservice.md)
* [TweenService](../classes/tween-service.md)
* [UserInputService](../classes/user-input-service.md)

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
> A direct alias for the Players service.

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

### BindToClose()

> `game:BindToClose(callback: Function)`
>
> Registers a callback that runs when the server is closing.

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
> A container for scripts that run on each client. [StarterPlayerScripts](../classes/starter-player-scripts.md)

<br/>

### ServerScriptService

> `Instance`
>
> ServerScriptService contains [Scripts](../classes/script.md) that run when the server starts. [ServerScriptService](../classes/server-script-service.md)

<br/>

### StarterGui

> `Instance`
>
> [StarterGui](../classes/starter-gui.md)

<br/>

### StarterPack

> `Instance`
>
> [StarterPack](../classes/starter-pack.md)

<br/>

### DataStoreService

> `Instance`
>
> Available in server Scripts only. [DataStoreService](../classes/data-store-service.md)

<br/>

### MarketplaceService

> `Instance`
>
> Available in server Scripts only. [MarketplaceService](../classes/marketplace-service.md)

<br/>

### Lighting

> Unavailable at runtime
>
> `game:GetService("Lighting")` is not a valid service in either Script or LocalScript. [Lighting](../classes/lighting.md)

<br/>

## Notes

`game.Workspace` and `game:GetService("Workspace")` are the same object, and `ClassName` and `Name` report `Workspace`. `game.Players` is the same object as `game:GetService("Players")`.

`game.OnClose` is read-only. Use `game:BindToClose(callback)` to run code when the server closes.
