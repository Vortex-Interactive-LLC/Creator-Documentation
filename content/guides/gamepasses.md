---
title: Gamepasses
description: Sell one-time purchases for your game and check who owns them.
---
A gamepass is a one-time purchase that belongs to a game. A player buys it once and keeps it. [`MarketplaceService`](../reference/classes/marketplace-service.md) prompts the purchase and checks ownership. It is only available in server scripts.

```luau
-- Script
local MarketplaceService = game:GetService("MarketplaceService")
local Players = game:GetService("Players")

local GAME_PASS_ID = 12

Players.PlayerAdded:Connect(function(player)
    if MarketplaceService:UserOwnsGamePassAsync(player.UserId, GAME_PASS_ID) then
        print(player.Name, "owns the gamepass")
    else
        MarketplaceService:PromptGamePassPurchase(player, GAME_PASS_ID)
    end
end)

MarketplaceService.PromptGamePassPurchaseFinished:Connect(function(player, gamePassId, purchased, result)
    if purchased then
        print(player.Name, "bought gamepass", gamePassId)
    else
        print(player.Name, "did not buy:", result)
    end
end)
```

## Prompting

`PromptGamePassPurchase(player, gamePassId)` opens the purchase window for that player and returns straight away. It does not wait for the player's answer. Listen to `PromptGamePassPurchaseFinished` for the outcome.

## The result

`PromptGamePassPurchaseFinished` fires once for every prompt, with `(player, gamePassId, purchased, result)`. `purchased` is `true` when the gamepass was bought. `result` is a short code:

| `result` | Meaning |
| --- | --- |
| `purchased` | The purchase went through. |
| `cancelled` | The player closed the window, or it was replaced by another prompt. |
| `expired` | The prompt was left open too long. |
| `owned` | The player already owns the gamepass. |
| `insufficient_funds` | The player did not have enough Volts. |
| `unavailable` | The gamepass or the store could not be reached or is not for sale. |

Other codes can appear if a request fails, so treat any `purchased == false` as "did not buy" and use `result` only for logging or messages.

## Checking ownership

`UserOwnsGamePassAsync(user, gamePassId)` returns whether the user owns the gamepass. `user` is a user id, such as `player.UserId`, or a `Player`. It waits for the answer.

## Describing a gamepass

`GetProductInfo(gamePassId, Enum.InfoType.GamePass)` returns a table describing the gamepass and raises an error if it does not exist:

```luau
local info = MarketplaceService:GetProductInfo(GAME_PASS_ID, Enum.InfoType.GamePass)
print(info.Name, info.PriceInVolts)
```

| Field | Meaning |
| --- | --- |
| `Name` | The gamepass's name. |
| `Description` | The gamepass's description. |
| `PriceInVolts` | The price. |
| `IsForSale` | Whether the gamepass can currently be bought. |
| `GameId` | The id of the game the gamepass belongs to. |
| `Creator` | A table with the owner's `Id`, `Name`, and `CreatorType`, which is `User` or `Group`. |

> [!NOTE]
> In Vortex Studio playtests, purchases are test purchases. The window says so, no Volts are spent, and `UserOwnsGamePassAsync` returns `false`.

## Creating a gamepass

Create gamepasses on [Vortex Create](https://create.playvortex.io), on your game's page.

- The lowest price is 5 Volts and the highest is 1,000,000 Volts;
- You receive 80% of each sale;
- A game can have up to 50 gamepasses that are not archived;
- An icon is optional. Every icon is reviewed before it appears, and you can follow its status on the gamepass's page;
- Players buy gamepasses from the Store tab on your game's page.

## Archiving and deleting

Archive a gamepass to take it off sale. Players who already own it keep it, and you can restore it later. You can delete a gamepass that no one has bought. Once it has been bought, you can only archive it.
