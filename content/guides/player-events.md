---
title: Players Joining & Leaving
description: React to players joining, spawning, dying and leaving.
---
The [`Players`](../reference/classes/players.md) service tells a server `Script` when players join and leave, and each [`Player`](../reference/classes/player.md) tells you when their character spawns or is removed.

## Joining and leaving

```luau
-- Script
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
    print(player.Name, "joined with user id", player.UserId)
end)

Players.PlayerRemoving:Connect(function(player)
    print(player.Name, "is leaving")
end)
```

`PlayerAdded` passes a real `Player` instance. When your handler runs, `Players:GetPlayers()` already includes the new player, and `player.Character` is already set. When `PlayerRemoving` runs, `GetPlayers()` no longer includes the leaving player, but `player.Parent` is still `Players` for the length of the handler.

## Characters

```luau
Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local humanoid = character:FindFirstChild("Humanoid")

        humanoid.Died:Connect(function()
            print(player.Name, "died")
        end)
    end)

    player.CharacterRemoving:Connect(function(character)
        print(player.Name, "character removed")
    end)
end)
```

`CharacterAdded` fires every time the player's character spawns, including after a respawn, so connect to it once per player rather than once per spawn. When a player leaves, `CharacterRemoving` fires before `PlayerRemoving`.

To go from a character back to its player, use `Players:GetPlayerFromCharacter(character)`. This is useful in a `Touched` handler, where the touching part's parent is the character:

```luau
part.Touched:Connect(function(hit)
    local player = Players:GetPlayerFromCharacter(hit.Parent)
    if player then
        print(player.Name, "touched the part")
    end
end)
```

## Looking players up

- `Players:GetPlayers()` returns every connected player.
- `Players:GetPlayerByUserId(userId)` returns the player with that user id.
- `Players.LocalPlayer` is the current player in a `LocalScript` and `nil` in a server `Script`.

> [!NOTE]
> A [`RemoteEvent`](../reference/classes/remote-event.md)'s `OnServerEvent` handler receives the `Player` that fired it as its first argument. See [Remote Events](remote-events.md).
