---
title: RemoteEvent
description: An event that sends information between client and server.
---

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of `RemoteEvent`.
<br><br>

* [FireServer](#fireserver)
* [FireClient](#fireclient)
* [FireAllClients](#fireallclients)

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `RemoteEvent`.
<br><br>

* [OnServerEvent](#onserverevent): `Connection`
* [OnClientEvent](#onclientevent): `Connection`

</details>

## Overview

Can be used to communicate from the server to a client (or all of them) and
vice-versa.

There is also [RemoteFunction](./remote-function.md), which is primarily used for getting data from one run context to another.

### Code Samples

`RemoteEvent` in `ReplicatedStorage`.

```luau
-- Script

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local MyRemote = ReplicatedStorage:WaitForChild("MyRemote") -- WaitForChild is important.

-- local activePlayers = Players:GetPlayers()
-- local random_player = activePlayers[math.random(1, #activePlayers)]
-- MyRemote:FireClient(random_player, "Message coming from the server!")
-- MyRemote:FireAllClients("Minions, tonight, we'll steal the moon!!!")

local function reply_received(sender, reply)
    print("Reply received from connection " .. sender .. ": " .. reply)
end

MyRemote.OnServerEvent:Connect(reply_received)
```

```luau
-- LocalScript

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local MyRemote = ReplicatedStorage:WaitForChild("MyRemote")

function received_msg(msg)
    print("Message received: " .. msg .. ". Replying.")
    MyRemote:FireServer("Copy that.")
end

MyRemote.OnClientEvent:Connect(received_msg)
```

## Methods

### FireServer

> `FireServer(arguments: Tuple?)`
>
> Transmits data from the client to the server. Returns nothing. **Available only in a `LocalScript`.**

#### Parameters

- `arguments: Tuple` — passed values.

### FireClient

> `FireClient(player: Player, arguments: Tuple?)`
>
> Transmits data from the server to the single client. Returns nothing. **Available only in a `Script`.**

#### Parameters

- `player: Player` — a client that is triggered by the server.
- `arguments: Tuple` — passed values.

### FireAllClients

> `FireAllClients(arguments: Tuple?)`
>
> Transmits data from the server to all clients. Returns nothing. **Available only in a `Script`.**

#### Parameters

- `arguments: Tuple` — passed values.

## Signals

### OnServerEvent

> `OnServerEvent(sender: Player, arguments: Tuple?): Connection`
>
> Fires when any client sends a data to this `RemoteEvent`. Returns `Connection`. **Available only in a `Script`.**

#### Parameters

- `sender: Tuple` — the client that sent the data.
- `arguments: Tuple` — passed values.

### OnClientEvent

> `OnClientEvent(arguments: Tuple?): Connection`
>
> Fires when the server sends a data to this `RemoteEvent`. Returns `Connection`. **Available only in a `LocalScript`.**

#### Parameters

- `arguments: Tuple` — passed values.

## Vortex Studio 0.8.1 notes

- `FireServer` to `OnServerEvent` was confirmed for an editor-authored remote
  in `ReplicatedStorage`.
- Script-created remotes parented into `ReplicatedStorage` were visible to the
  client but did not dispatch to the server handler.
- `FireClient`, `FireAllClients`, and `OnClientEvent` are exposed.
- Instances, including `LocalPlayer` and the character, cannot be sent as
  remote arguments.
