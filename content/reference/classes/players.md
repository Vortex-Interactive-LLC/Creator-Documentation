---
title: Players
description: A container that holds all currently connected players as Player objects.
---

## Summary

A service representing connected clients as [Player](./player.md) instances.

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
- `LocalPlayer` - available in a `LocalScript`; otherwise `nil`;
- `RespawnTime` - `number`, defaults to `5`. How many seconds a player waits after dying before their character respawns.

## Methods

- `GetPlayers(): { Player }` - returns the list of currently visible players.
* `GetPlayerByUserId(UserId: number): Player` - Returns the player with the specified UserId.
* `GetPlayerFromCharacter(character: Character): Player` - Returns the player associated with the specified character.
* `GetNameFromUserIdAsync(userId: number): string` - Returns the username for the specified UserId. Server `Script` only. Yields while the name is looked up.
* `GetUserIdFromNameAsync(name: string): number` - Returns the UserId for the specified username. Server `Script` only. Yields while the id is looked up.
* `GetHumanoidDescriptionFromUserIdAsync(userId: number): HumanoidDescription` - Returns the outfit of the specified user as a [HumanoidDescription](./humanoid-description.md). Server `Script` only. Yields while the outfit is looked up, and errors if the user does not exist.
* `CreateHumanoidModelFromUserIdAsync(userId: number): Model` - Returns a new rig wearing the outfit of the specified user, named after the user. The rig has a [Humanoid](./humanoid.md) holding a [HumanoidDescription](./humanoid-description.md) with the outfit, a `HumanoidRootPart` and leg, head and arm parts, and is not parented, so set its `Parent` to `workspace`. The rig wears [`BodyColors`](./body-colors.md), [`Shirt`](./shirt.md), [`Pants`](./pants.md), and [`Accessory`](./accessory.md) objects. Change them, or call `ApplyDescription` with its `HumanoidDescription`, to change how it looks. Server `Script` only. Yields while the outfit is looked up, and errors if the user does not exist.

## Signals

* `PlayerAdded(): Signal` - Fires when a player joins the server, signaling a player has joined the server.
* `PlayerRemoving(): Signal` - Fires when a player leaves the server, signaling a player has left the server.

`GetChildren` and `FindFirstChild` are also available, and a player can be looked up by name with `Players[name]`.

## Notes

`GetPlayers()` returns the connected players in both a `LocalScript` and a server `Script`. `LocalPlayer` is `nil` on the server.

The `Player` that fired a [`RemoteEvent`](./remote-event.md) is passed as the first argument to its `OnServerEvent` handler, so there is no need to look it up from the `Players` service.
