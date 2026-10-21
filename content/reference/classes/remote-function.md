---
title: RemoteFunction
description: A function that can be invoked between the server and client and return values.
---

## Summary

Unlike [RemoteEvents](./remote-event.md), `RemoteFunctions` allow data to be computed during a function call and return the computed values.
`InvokeAllClients` does not exist because waiting for every player to return a value cannot be guaranteed

### Example

```luau
-- server

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")

local GetPiFromDigits = ReplicatedStorage:WaitForChild("GetPiFromDigits")

-- Roblox-style targeting example; see the Vortex notes below.
local activePlayers = Players:GetPlayers()
local random_player = activePlayers[math.random(1, #activePlayers)]
local pi = GetPiFromDigits:InvokeClient(random_player, 5)

print(random_player.Name .. " replied with: " .. pi)
```

```luau
-- LocalScript

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local GetPiFromDigits = ReplicatedStorage:WaitForChild("GetPiFromDigits")

function compute_pi(digits)
    -- magic
    local col = math.floor(digits * 10 / 3)
    local array = {}
    for i = 1, col, 1 do table.insert(array, 2) end
    local output = {}

    for _ = 1, digits, 1 do
        local carry = 0
        for i = col - 1, 0, -1 do
            local num = array[i] * 10 + carry
            local denom = i * 2 + 1
            arr[i] = num % denom
            carry = math.floor(num / denom)
        end

        num = arr[1] * 10 + carry
        arr[1] = num % 10
        output.append(tostring(math.floor(num / 10)))
    end

    local result = output[1] .. "."
    for i = 2, #output, 1 do
        result ..= output[i]
    end

    return result
end

GetPiFromDigits.OnClientInvoke = compute_pi
```

## Methods

- `InvokeClient(player: Player, arguments: Tuple) : Tuple` - Invokes a function
  on the client from the server and returns the result;
- `InvokeServer(arguments: Tuple) : Tuple` - Invokes a function on
   the server from the client and returns the result.

## Callbacks

- `OnClientInvoke(arguments: Tuple) : Tuple` - A writable callback invoked
   on the client by the server;
- `OnServerInvoke(senderId: Number, arguments: Tuple) : Tuple` - A writable
   callback invoked on the server by the client.

## Vortex Studio 0.3.4 notes

`InvokeServer` is exposed on the client and assigning `OnServerInvoke` succeeds
in a Script for an editor-authored remote in `ReplicatedStorage`. However,
`InvokeServer(LocalPlayer)` is rejected before delivery because Instances cannot
currently be sent through remotes.A successful primitive request-response
round trip has not yet been established.

The server-side `Players:GetChildren()` route remains unavailable. In 0.3.4,
`Players:GetPlayers()` does return visible Player objects in a server Script,
so, in principle, it provides the Player target shown above. `OnClientInvoke` and
`InvokeClient` delivery are still untested.
