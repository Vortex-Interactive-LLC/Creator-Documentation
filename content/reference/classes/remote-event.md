---
title: RemoteEvent
description: An event that sends information between clients and the server.
---

## Summary

A `RemoteEvent` can be used to communicate from the server to a client (or all clients) and vice versa.

For additional information, see [RemoteFunction](./remote-function.md).

### Example

```luau
-- server

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local MyRemote = ReplicatedStorage:WaitForChild("MyRemote") -- WaitForChild is important.

local activePlayers = Players:GetPlayers()
local random_player = activePlayers[math.random(1, #activePlayers)]
MyRemote:FireClient(random_player, "Message coming from the server!")
MyRemote:FireAllClients("Minions, tonight, we'll steal the moon!!!")

local function reply_received(player, reply)
    print("Reply received from " .. player.Name .. ": " .. reply)
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

- `FireAllClients(arguments: Tuple) : ()` - Sends data to all clients;
- `FireClient(player: Player, arguments: Tuple) : ()` - Sends data from the server to a client;
- `FireServer(arguments: Tuple) : ()` - Sends data from the client to the server.

## Events

- `OnClientEvent(arguments: Tuple) : Signal` - Fires when the client receives data from the server;
- `OnServerEvent(player: Player, arguments: Tuple) : Signal` - Fires when the server receives data from the client.

## Notes

- Create RemoteEvents in `ReplicatedStorage` through the editor before play. Editor-authored remotes dispatch from `FireServer` to `OnServerEvent`; remotes created by a script at runtime do not dispatch to the server handler.
- `OnServerEvent` receives the `Player` who fired the event as its first argument.
- Arguments can be numbers, strings, booleans, `nil`, `Vector3`, `Color3`, and tables of those. Instances, including a `Player` and the character, cannot be sent.
- `FireServer` can only be called from a client script.
