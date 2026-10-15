---
title: RemoteEvent
description: An event that sends information between clients and the server.
---

## Summary

A `RemoteEvent` can be used to communicate from the server to a client (or all clients)
and vice versa.

For additional information, see
[RemoteFunction](./remote-function.md).

### Example

```luau
-- server

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local MyRemote = ReplicatedStorage:WaitForChild("MyRemote") -- WaitForChild is important.

-- The server can enumerate Players in 0.3.4, but FireClient delivery is still
-- unconfirmed, so this Roblox-style targeting block remains illustrative:
-- local activePlayers = Players:GetPlayers()
-- local random_player = activePlayers[math.random(1, #activePlayers)]
-- MyRemote:FireClient(random_player, "Message coming from the server!")
-- MyRemote:FireAllClients("Minions, tonight, we'll steal the moon!!!")

-- `senderId` is a numeric connection identifier in Vortex, not a Player.
local function reply_received(senderId, reply)
    print("Reply received from connection " .. senderId .. ": " .. reply)
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
- `FireClient(player: Player, arguments: Tuple) : ()` - Sends data from the
   server to a client;
- `FireServer(arguments: Tuple) : ()` - FSends data from the client to the
  server.
## Events

- `OnClientEvent(arguments: Tuple) : Signal` - Fires when the client receives
   data from the server
- `OnServerEvent(senderId: Number, arguments: Tuple) : Signal` - Fires when
   the server receives data from the client.

## Vortex Studio 0.3.4 notes

- `FireServer` to `OnServerEvent` delivery was confirmed for an editor-authored remote
  in `ReplicatedStorage`.
- Script-created remotes parented to `ReplicatedStorage` were visible to the
  client but did not dispatch to the server handler.
- `FireClient`, `FireAllClients`, and `OnClientEvent` are exposed, but their
  delivery has not yet been established.
- The server can enumerate Player objects through `Players:GetPlayers()`, but
  cannot map `senderId` to a specific Player, Character, or Humanoid. Normal
  Roblox-style targeting of the caller therefore does not currently apply.
- Instances, including `LocalPlayer` and the character, cannot be sent as
  remote arguments.
