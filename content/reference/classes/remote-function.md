---
title: RemoteFunction
description: A function that is invoked and returns values from the server to the client, and vice-versa.
---

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of `RemoteFunction`.
<br><br>

* [InvokeServer](#invokeserver): `Tuple`
* [InvokeClient](#invokeclient): `Tuple`

</details>

<details>
<summary><b>Callbacks</b></summary>
Callbacks of `RemoteFunction`.
<br><br>

* [OnServerInvoke](#onserverinvoke): `Connection`
* [OnClientInvoke](#onclientinvoke): `Connection`

</details>

## Overview

Differently from [RemoteEvents](./remote-event.md), `RemoteFunctions` allows data to be computed inside a function call and returned with the computed values. `InvokeAllClients` does not exist, since yielding until every player returns a value is not guaranteed.

## Code Samples

`RemoteFunction` in `ReplicatedStorage`

```luau
-- LocalScript

local remoteFunction = game:GetService('ReplicatedStorage').RemoteFunction

local var1,var2,var3,var4 = remoteFunction:InvokeServer('hello server!')
```

```luau
-- Script

local removeFunction = game:GetService('ReplicatedStorage').RemoteFunction

local function _onServerInvoke(player: Player, arguments: Tuple)
	print(`Callback to connection: {player} with {arguments}`)
	return 'hi',1,true,{}
end

removeFunction.OnServerInvoke = _onServerInvoke
```

## Methods

### InvokeServer

> `InvokeServer(arguments: Tuple): Tuple`
>
> Invokes `RemoteFunction` to get data from the server. Returns `Tuple`. **Available only in a `LocalScript`.**

#### Parameters

- `arguments: Tuple` — passed values.

### InvokeClient

> `InvokeClient(player: Player, arguments: Tuple): Tuple`
>
> Invokes `RemoteFunction` to get data from the client. Returns `Tuple`. **Available only in a `Script`.**

#### Parameters

- `player: Player` — client to invoke.
- `arguments: Tuple` — passed values.

## Callbacks

### OnServerInvoke

> `OnServerInvoke(player: Player, arguments: Tuple): Connection`
>
> Callback invoked from the client to the server. Returns `Connection`. **Available only in a `Script`.**

#### Parameters

- `player: Player` — invoked client.
- `arguments: Tuple` — passed values.

### OnClientInvoke

> `OnClientInvoke(arguments: Tuple): Connection`
>
> Callback invoked from the server to the client. Returns `Connection`. **Available only in a `LocalScript`.**

#### Parameters

- `arguments: Tuple` — passed values.

## Vortex Studio 0.3.4 notes

`InvokeServer` is exposed on the client and assigning `OnServerInvoke` succeseds
in a `Script` for an editor-authored remote in `ReplicatedStorage`. However,

`InvokeServer(LocalPlayer)` is rejected before delivery because Instances cannot
currently be sent through remotes. A successful primitive request/response
round trip has not yet been established.
