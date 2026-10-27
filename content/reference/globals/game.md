---
title: Game
description: The root instance of a game.
---

> [!NOTE]
> There will be more things (methods, constructors, properties, etc.) in the future.

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `game`.
<br><br>

* [Workspace](#workspace): `Workspace`
* [Players](#players): `Players`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `game`.
<br><br>

* [GetService(serviceName: `string`)](#getservice): `Instance`
* [BindToClose(function: `function`)](#bindtoclose): `Instance`

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

## Overview

`game` is the root instance and provides access to services.

## Properties

### Workspace

> [`Workspace`](../classes/workspace.md)
>
> The root `Workspace` service.

### Players

> [`Players`](../classes/players.md)
>
> A direct alias for the Players service. In Vortex Studio 0.3.4 it is a
> distinct proxy table from `game:GetService("Players")`.

## Methods

### GetService()

> `game:GetService(serviceName: string)`
>
> Returns the service with the specified name.

#### Parameters

- `serviceName`: `string` — the name of the service to retrieve.

### BindToClose()

> `game:BindToClose(function: function)`
>
> Binds a function to be called before the game closes.

#### Parameters

- `function`: `function` — a function called before the the game closes.

#### Code Sample

```
local function onBindToClose()
    print('shutdowned')
end

game:BindToClose(onBindToClose)
```

## Services

### Workspace

> `Instance`
>
> The Workspace is the root object that holds anything that is currently in the world. [Workspace](../classes/workspace.md)

### Players

> `Instance`
>
> The service that contains the currently connected player objects. [Players](../classes/players.md)

### ReplicatedStorage

> `Instance`
>
> A container for instances loaded by both the server and the client. [ReplicatedStorage](../classes/replicated-storage.md)

### StarterPlayerScripts

> `Instance`
>
> Container inside the StarterPlayer service that stores client-side scripts. [StarterPlayerScripts](../classes/starter-player-scripts.md)

### ServerScriptService

> `Instance`
>
> Contains [Scripts](../classes/script.md) that run when the server starts. [ServerScriptService](../classes/server-script-service.md)

### Lighting

> Unavailable in the tested runtime
>
> `game:GetService("Lighting")` rejects this service in both Script and
> LocalScript in Vortex Studio 0.3.4. [Lighting](../classes/lighting.md)

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later
releases.

`game.Workspace` and `game:GetService("Workspace")` both report `ClassName`
and `Name` as `Workspace`.

The `CloseReason` enum does not yet exist in the `BindToClose` method.
