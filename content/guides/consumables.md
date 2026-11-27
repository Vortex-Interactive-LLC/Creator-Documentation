---
title: Consumables
description: Sell purchases a player can buy again and again, and deliver them reliably.
---
A consumable is a purchase that belongs to a game and can be bought any number of times, such as a currency pack or a boost. Buying one does not give the player anything by itself. Your server script grants it from a receipt callback. [`MarketplaceService`](../reference/classes/marketplace-service.md) prompts the purchase and delivers receipts. It is only available in server scripts.

```luau
-- Script
local MarketplaceService = game:GetService("MarketplaceService")
local DataStoreService = game:GetService("DataStoreService")
local Players = game:GetService("Players")

local COINS_PACK_ID = 3

local handled = DataStoreService:GetDataStore("HandledReceipts")
local coins = DataStoreService:GetDataStore("Coins")

MarketplaceService.ProcessConsumableReceipt = function(receipt)
    local key = tostring(receipt.PurchaseId)
    if handled:GetAsync(key) then
        return Enum.ConsumableDecision.Granted
    end
    coins:IncrementAsync(tostring(receipt.PlayerId), 100)
    handled:SetAsync(key, true)
    return Enum.ConsumableDecision.Granted
end

Players.PlayerAdded:Connect(function(player)
    MarketplaceService:PromptConsumablePurchase(player, COINS_PACK_ID)
end)
```

## Prompting

`PromptConsumablePurchase(player, consumableId)` opens the purchase window for that player and returns straight away. It does not wait for the player's answer. Listen to `PromptConsumablePurchaseFinished` for the outcome.

A consumable can only be sold in the game that owns it. If no `ProcessConsumableReceipt` function is set when the prompt is requested, the prompt is refused with `unavailable` and a warning is written to the output, so a player is never charged for something the game cannot grant.

## The result

`PromptConsumablePurchaseFinished` fires once for every prompt, with `(player, consumableId, purchased, result)`. `purchased` is `true` when the purchase went through. `result` is a short code:

| `result` | Meaning |
| --- | --- |
| `purchased` | The purchase went through. |
| `cancelled` | The player closed the window, or it was replaced by another prompt. |
| `expired` | The prompt was left open too long. |
| `insufficient_funds` | The player did not have enough Volts. |
| `unavailable` | The consumable or the store could not be reached or is not for sale, or no receipt function is set. |

Other codes can appear if a request fails, so treat any `purchased == false` as "did not buy" and use `result` only for logging or messages.

## Receipts

Every purchase creates a receipt that stays open until your callback confirms it. Set `MarketplaceService.ProcessConsumableReceipt` to a function that grants the purchase and returns `Enum.ConsumableDecision.Granted`. It receives a table:

| Field | Meaning |
| --- | --- |
| `PurchaseId` | A number that is unique to this purchase. |
| `PlayerId` | The id of the player who bought it. |
| `ConsumableId` | The id of the consumable. |
| `PlaceIdWherePurchased` | The id of the game the purchase was made in. |
| `CurrencySpent` | The price paid, in Volts. |

The receipt is considered handled only when the function returns `Enum.ConsumableDecision.Granted` or `true`. Returning `Enum.ConsumableDecision.NotProcessedYet`, returning anything else, raising an error, or taking longer than 60 seconds leaves it open.

Open receipts are delivered again:

- right after the purchase;
- every time the player joins a server of the game;
- every 30 seconds while the player is in a server and a receipt is still open.

Receipts for one player run one at a time, in purchase order. Setting `ProcessConsumableReceipt` again replaces the previous function. While none is set, nothing is delivered and receipts stay open.

> [!WARNING]
> Delivery happens at least once, not exactly once. A receipt can arrive again if your function granted the purchase and then failed or timed out, or if two servers deliver it near the same moment. Record each `PurchaseId` you have granted, for example in a [DataStore](datastores.md), and return `Granted` without granting again when you see one twice.

## Listing consumables

`GetConsumablesAsync()` returns a pages object for the game's consumables that are on sale. `GetCurrentPage()` returns an array with one table per consumable. `IsFinished` is always `true`, and `AdvanceToNextPageAsync()` does nothing.

```luau
for _, entry in MarketplaceService:GetConsumablesAsync():GetCurrentPage() do
    print(entry.ConsumableId, entry.Name, entry.PriceInVolts)
end
```

| Field | Meaning |
| --- | --- |
| `ConsumableId` | The consumable's id. |
| `Name` | The consumable's name. |
| `Description` | The consumable's description. |
| `PriceInVolts` | The price. |

## Describing a consumable

`GetConsumableInfo(consumableId)` returns a table describing the consumable and raises an error if it does not exist. `GetProductInfo(consumableId, Enum.InfoType.Consumable)` returns the same table.

```luau
local info = MarketplaceService:GetConsumableInfo(COINS_PACK_ID)
print(info.Name, info.PriceInVolts)
```

| Field | Meaning |
| --- | --- |
| `Name` | The consumable's name. |
| `Description` | The consumable's description. |
| `PriceInVolts` | The price. |
| `IsForSale` | Whether the consumable can currently be bought. |
| `GameId` | The id of the game the consumable belongs to. |
| `Creator` | A table with the owner's `Id`, `Name`, and `CreatorType`, which is `User` or `Group`. |

> [!NOTE]
> In Vortex Studio playtests, purchases are test purchases. The window says so, no Volts are spent, and receipts are delivered to your callback but are not kept after the playtest ends.

## Creating a consumable

Create consumables on [Vortex Create](https://create.playvortex.io), on your game's page.

- The lowest price is 5 Volts and the highest is 1,000,000 Volts;
- You receive 80% of each sale;
- A game can have up to 50 consumables that are not archived;
- An icon is optional. Every icon is reviewed before it appears, and you can follow its status on the consumable's page;
- Consumables can only be bought from inside the game. They do not appear in the Store tab.

## Archiving and deleting

Archive a consumable to take it off sale. Purchases already made are still delivered, and you can restore it later. You can delete a consumable that no one has bought. Once it has been bought, you can only archive it.
