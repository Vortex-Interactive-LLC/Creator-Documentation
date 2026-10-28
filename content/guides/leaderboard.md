---
title: Leaderboards
description: Learn how to create and update player leaderboards using leaderstats.
---

> Leaderboards display player statistics using a `Folder` named `leaderstats` parented to a player.
> Value objects such as `IntValue`, `StringValue`, and `BoolValue` can be placed inside this folder to display stats on the built-in leaderboard.

The leaderboard is a built-in feature that lists all players and their stats.

### Creating a Leaderboard

A leaderboard can be created by adding a `Folder` named `leaderstats` to a player. Value objects parented to this folder are displayed on the built-in leaderboard.

Here's a simple example:

```lua
local Players = game.Players

Players.PlayerAdded:Connect(function(player)
    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player

    local cash = Instance.new("IntValue")
    cash.Name = "Cash"
    cash.Value = 50
    cash.Parent = leaderstats
end)
```

 This example creates a `Cash` statistic for each player, initialized to `50`.

> [!NOTE]
> The folder must be named `leaderstats` for its values to appear on the built-in leaderboard.

### Updating Statistics

Statistics can be updated by changing the `Value` property of their corresponding value objects.

For example, the following code adds 10 cash to a player's existing cash value:

```lua
player.leaderstats.Cash.Value += 10
```

Changes to these values are reflected on the leaderboard.

### Supported Value Types

 The following value types have been tested and confirmed to work on Vortex leaderboards:

* `IntValue`
* `StringValue`
* `BoolValue`

> Choose a value type based on the kind of statistic you want to display.
