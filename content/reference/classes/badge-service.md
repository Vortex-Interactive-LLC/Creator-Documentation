---
title: BadgeService
description: A server-only service for awarding and checking game badges.
---

## Summary

Get the service with `game:GetService("BadgeService")`. It is only available in server scripts. See the [Badges guide](../../guides/badges.md).

### Example

```luau
local BadgeService = game:GetService("BadgeService")

BadgeService:AwardBadge(player, 1234)
```

## Methods

- `AwardBadge(user: Player | number, badgeId: number): boolean` - awards the badge to the user. `user` is a user id or a player. Returns `true` the first time and `false` if the user already has it. Raises an error if the badge does not exist, belongs to another game, is disabled, or the user has never joined the game. Waits for the answer;
- `UserHasBadgeAsync(user: Player | number, badgeId: number): boolean` - returns whether the user has the badge. Waits for the answer;
- `GetBadgeInfoAsync(badgeId: number): table` - describes a badge, returning `Name`, `Description`, `IsEnabled`, `GameId`, and `AwardedPercentage`. Raises an error if it does not exist. Waits for the answer.

## Signals

- `BadgeAwarded(player: Player, badgeId: number)` - fires when `AwardBadge` awards a badge for the first time.
