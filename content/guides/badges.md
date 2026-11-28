---
title: Badges
description: Reward players for achievements in your game and check who has earned them.
---
A badge is an achievement that belongs to a game, such as finishing a level or finding a secret. Your server script awards it with [`BadgeService`](../reference/classes/badge-service.md). The player sees a notification, and the badge appears on their profile and on your game's page. It is only available in server scripts.

```luau
-- Script
local BadgeService = game:GetService("BadgeService")
local Players = game:GetService("Players")

local FIRST_STEPS_ID = 4

Players.PlayerAdded:Connect(function(player)
    if BadgeService:UserHasBadgeAsync(player, FIRST_STEPS_ID) then
        return
    end
    if BadgeService:AwardBadge(player, FIRST_STEPS_ID) then
        print(player.Name, "earned First Steps")
    end
end)

BadgeService.BadgeAwarded:Connect(function(player, badgeId)
    print(player.Name, "was awarded badge", badgeId)
end)
```

## Awarding

`AwardBadge(user, badgeId)` gives the badge to a player and waits for the answer. `user` is a player or a user id. It returns `true` the first time the badge is awarded and `false` if the player already has it, so it is safe to call every time the player does the thing.

When it returns `true`, the player sees a notification and `BadgeAwarded` fires with `(player, badgeId)`. It does not fire for a repeat award.

`AwardBadge` raises an error if the request is refused. The error ends with a short code:

| Code | Meaning |
| --- | --- |
| `not_found` | The badge does not exist. |
| `wrong_game` | The badge belongs to another game. |
| `disabled` | The badge is turned off. |
| `not_played` | The player has never joined this game. |

A badge can only be awarded by a server of the game that owns it. Use `pcall` if a failed award should not stop your script.

## Checking

`UserHasBadgeAsync(user, badgeId)` returns whether the user has the badge. `user` is a player or a user id. Waits for the answer.

## Describing a badge

`GetBadgeInfoAsync(badgeId)` returns a table describing the badge and raises an error if it does not exist.

```luau
local info = BadgeService:GetBadgeInfoAsync(FIRST_STEPS_ID)
print(info.Name, info.AwardedPercentage)
```

| Field | Meaning |
| --- | --- |
| `Name` | The badge's name. |
| `Description` | The badge's description. |
| `IsEnabled` | Whether the badge can currently be awarded. |
| `GameId` | The id of the game the badge belongs to. |
| `AwardedPercentage` | The percent of the game's players who have earned it, from 0 to 100. |

> [!NOTE]
> In Vortex Studio playtests, awards are test awards. The notification appears, but nothing is saved and the badge is not earned on your account. Awards last until the playtest ends.

## Creating a badge

Create badges on [Vortex Create](https://create.playvortex.io), on your game's page.

- Badges are free to create and a game can have any number of them;
- A name can be up to 80 characters and a description up to 1,000;
- An icon is optional. Every icon is reviewed before it appears, and you can follow its status on the badge's page;
- Badges can only be awarded from inside the game.

## Disabling and deleting

Turn a badge off to stop it being awarded. Players who already have it keep it. You can delete a badge that no one has earned. Once it has been earned, you can only disable it.
