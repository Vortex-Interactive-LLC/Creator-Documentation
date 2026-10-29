---
title: Remote Events
description: One way communication between the server and clients.
---
> [!Summary]
> RemoteEvents send one-way messages between the server and clients for events like input, state changes, or game actions. Use `FireServer` from the client and `OnServerEvent` on the server, or use `FireClient`/`FireAllClients` from the server and handle `OnClientEvent` on the client.

# Remote Events
A `RemoteEvent` enables one-way communication between the server and clients. It doesn't wait for a response and has no return value. It's built for telling the other side what happened, not asking the other side for a result. For a call that needs a response, use [RemoteFunction](./remote-functions.md) instead.

The primary parent container for remote events is `ReplicatedStorage`, as both the server and client can see and access it.
> [!WARNING]
> **Security note:** never trust arguments a client sends via `FireServer` at face value - a modified client can call it with anything. Re-validate any arguments on the server before acting on them.

## Example
In this example, pressing `E` changes a part named `ColorBlock` to a random color. Key presses can only be detected on the client, but the color change needs to happen on the server so every player sees the same result, which is what the remote event is for.

## Server Script
- placed in `ServerScriptService`
- Be sure to create an event named `ChangeColor` parented to `ReplicatedStorage`
```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local changeColor = ReplicatedStorage.ChangeColor
local colorBlock = workspace.ColorBlock

changeColor.OnServerEvent:Connect(function(player)
    colorBlock.Color = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))
end)
```

## Client Script
- placed in `StarterPlayerScripts`
```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")

local changeColor = ReplicatedStorage.ChangeColor

UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.E then
        changeColor:FireServer()
    end
end)
```

## Methods

| Method | Returns | Description |
|---|---|---|
| `FireServer(...)` | void | Called from a client. Sends arguments to the server. |
| `FireClient(...)` | void | Called from the server. Sends arguments to the chosen client. |
| `FireAllClients(...)` | void | Called from the server. Sends arguments to every client. |

## Events
| Event | Parameters | Description |
|---|---|---|
| `OnServerEvent` | player, ... | Fires on the server when a client calls FireServer. |
| `OnClientEvent` | ... | Fires on the client when the server calls FireClient or FireAllClients |

## Vortex Studio 0.3.4 notes

- Create RemoteEvents in `ReplicatedStorage` through the editor before play. Editor-authored remotes dispatch from `FireServer` to `OnServerEvent`; script-created remotes were visible to clients but did not dispatch in the tested runtime.
- The first `OnServerEvent` value is currently a numeric connection ID, not a `Player`. The server can enumerate Players through `GetPlayers()`, but no public mapping from this ID to the corresponding Player, Character, or Humanoid is known.
- Remote arguments cannot currently contain Instances, including `LocalPlayer` or a Character.
- `FireClient`, `FireAllClients`, and `OnClientEvent` are exposed, but their delivery remains unconfirmed.
