---
title: Players
description: A container that holds all currently connected players as Player objects.
---

## Summary

A service representing connected clients as
[Player](./player.md) instances.

### Example

```luau
-- LocalScript

local Players = game:GetService("Players")

local everyPlayer = Players:GetPlayers()
local player = Players.LocalPlayer
```

## Properties

- `Name` - the name of the service;
- `ClassName` - the runtime class name;
- `LocalPlayer` - available in a `LocalScript`; otherwise `nil`.

## Methods

- `GetPlayers(): { Player }` - returns the list of currently visible players.
* `GetPlayerByUserId(UserId: number): Player` - Returns the player with the specified UserId.
* `GetPlayerFromCharacter(character: Character): Player` - Returns the player associated with the specified character.

## Signals

* `PlayerAdded(): Signal` - Fires when a player joins the server, signaling a player has joined the server.
* `PlayerRemoving(): Signal` - Fires when a player leaves the server, signaling a player has left the server.

`GetChildren` is not exposed by the current Vortex Players service.

## Vortex Studio 0.3.4 notes

`GetPlayers()` returns the current player in a `LocalScript`. In a confirmed
server `Script`, it also returned a list containing the live `Player` object;
the returned `Player`'s `Character` is readable. `LocalPlayer` remains `nil` on the
server.

The numeric connection ID passed as the first `OnServerEvent` argument still
has no known public mapping back to a particular Player. Numeric and string-based service
indexing, along with the tested player lookup methods, does not provide that mapping.
