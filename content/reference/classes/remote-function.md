---
title: RemoteFunction
description: A function that can be invoked between the server and client and return values.
---

## Summary

Unlike [RemoteEvents](./remote-event.md), `RemoteFunctions` allow data to be computed during a function call and return the computed values. `InvokeAllClients` does not exist because waiting for every player to return a value cannot be guaranteed.

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

- `InvokeClient(player: Player, arguments: Tuple) : Tuple` - Invokes a function on the client from the server and returns the result;
- `InvokeServer(arguments: Tuple) : Tuple` - Invokes a function on the server from the client and returns the result.

## Callbacks

- `OnClientInvoke(arguments: Tuple) : Tuple` - A writable callback invoked on the client by the server;
- `OnServerInvoke(player: Player, arguments: Tuple) : Tuple` - A writable callback invoked on the server by the client.

## Notes

- Create RemoteFunctions in `ReplicatedStorage` through the editor before play.
- `OnServerInvoke` receives the `Player` who invoked the function as its first argument.
- Arguments and return values cannot be Instances: invoking with `LocalPlayer` fails before delivery because Instances cannot be sent through remotes.
- If a client invokes a RemoteFunction that has no `OnServerInvoke` assigned on the server, the call fails with an error.
