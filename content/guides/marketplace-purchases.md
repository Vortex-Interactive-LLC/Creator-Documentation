---
title: Prompting Purchases
description: Offer catalog items for Volts from inside your game.
---
[`MarketplaceService`](../reference/classes/marketplace-service.md) lets a server `Script` ask a player to buy an item from the [catalog](https://playvortex.io/catalog) without leaving the game. The player sees a confirmation window showing the item and its price in Volts, and the item is added to their inventory if they accept.

```luau
-- Script
local MarketplaceService = game:GetService("MarketplaceService")
local Players = game:GetService("Players")

local ITEM_ID = 1234

local function offer(player)
    if MarketplaceService:PlayerOwnsAsset(player, ITEM_ID) then
        return
    end

    MarketplaceService:PromptPurchase(player, ITEM_ID)
end

Players.PlayerAdded:Connect(offer)

MarketplaceService.PromptPurchaseFinished:Connect(function(player, itemId, purchased, result)
    if purchased then
        print(player.Name, "bought item", itemId)
    else
        print(player.Name, "did not buy:", result)
    end
end)
```

`MarketplaceService` is only available in server scripts. `itemId` is the id of a catalog item.

## Prompting

`PromptPurchase(player, itemId)` opens the purchase window for that player and returns straight away. It does not wait for the player's answer. Listen to `PromptPurchaseFinished` for the outcome.

## The result

`PromptPurchaseFinished` fires once for every prompt, with `(player, itemId, purchased, result)`. `purchased` is `true` when the item was bought. `result` is a short code:

| `result` | Meaning |
| --- | --- |
| `purchased` | The purchase went through. |
| `cancelled` | The player closed the window, or it was replaced by another prompt. |
| `expired` | The prompt was left open too long. |
| `owned` | The player already owns the item. |
| `insufficient_funds` | The player did not have enough Volts. |
| `limited` | The item is a limited item, which cannot be bought this way. |
| `unavailable` | The item or the store could not be reached or is not for sale. |

Other codes can appear if a request fails, so treat any `purchased == false` as "did not buy" and use `result` only for logging or messages.

## Checking and describing items

`PlayerOwnsAsset(player, itemId)` returns whether the player owns the item. It waits for the answer.

`GetProductInfo(itemId)` returns a table describing the item and raises an error if the item does not exist:

```luau
local info = MarketplaceService:GetProductInfo(ITEM_ID)
print(info.Name, info.PriceInVolts, info.Creator.Name)
```

| Field | Meaning |
| --- | --- |
| `Name` | The item's name. |
| `AssetType` | The kind of item. |
| `PriceInVolts` | The price. |
| `IsForSale` | Whether the item can currently be bought. |
| `IsLimited` | Whether the item is a limited item. |
| `Creator` | A table with the creator's `Id` and `Name`. |

> [!NOTE]
> In Vortex Studio playtests, purchases are test purchases. The window says so, no Volts are spent, and `PlayerOwnsAsset` returns `false`.
