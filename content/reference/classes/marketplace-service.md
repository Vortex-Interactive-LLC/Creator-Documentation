---
title: MarketplaceService
description: A server-only service for prompting item, gamepass, and consumable purchases.
---

## Summary

Get the service with `game:GetService("MarketplaceService")`. It is only available in server scripts. See the [Prompting Purchases guide](../../guides/marketplace-purchases.md) the [Gamepasses guide](../../guides/gamepasses.md), and the [Consumables guide](../../guides/consumables.md).

### Example

```luau
local MarketplaceService = game:GetService("MarketplaceService")

MarketplaceService:PromptPurchase(player, 1234)
```

## Methods

- `PromptPurchase(player: Player, itemId: number)` - opens the purchase window for the player and returns immediately. `itemId` must be a whole number from 1 to 2147483647;
- `PlayerOwnsAsset(player: Player, itemId: number): boolean` - returns whether the player owns the item. Waits for the answer;
- `GetProductInfo(id: number, infoType: Enum.InfoType?): table` - describes a catalog item, returning `Name`, `AssetType`, `PriceInVolts`, `IsForSale`, `IsLimited`, and `Creator` (`Id`, `Name`). With `Enum.InfoType.GamePass` or `Enum.InfoType.Consumable` it describes a gamepass or consumable instead, returning `Name`, `Description`, `PriceInVolts`, `IsForSale`, `GameId`, and `Creator` (`Id`, `Name`, `CreatorType`). Raises an error if it does not exist. Waits for the answer;
- `GetGamePassInfo(gamePassId: number): table` - describes a gamepass, returning the same table as `GetProductInfo` with `Enum.InfoType.GamePass`. Server `Script` only. Raises an error if it does not exist. Waits for the answer;
- `PromptGamePassPurchase(player: Player, gamePassId: number)` - opens the purchase window for a gamepass and returns immediately;
- `UserOwnsGamePassAsync(user: Player | number, gamePassId: number): boolean` - returns whether the user owns the gamepass. `user` is a user id or a player. Waits for the answer;
- `PromptConsumablePurchase(player: Player, consumableId: number)` - opens the purchase window for a consumable and returns immediately. Refused with `unavailable` if `ProcessConsumableReceipt` is not set. Also available as `PromptProductPurchase`;
- `GetConsumableInfo(consumableId: number): table` - describes a consumable, returning the same table as `GetProductInfo` with `Enum.InfoType.Consumable`. Raises an error if it does not exist. Waits for the answer;
- `GetConsumablesAsync(): Instance` - returns a pages object for the game's consumables on sale. `GetCurrentPage()` returns an array of tables with `ConsumableId`, `Name`, `Description`, and `PriceInVolts`. Entries also have `ProductId` and `DeveloperProductId`, the same as `ConsumableId`. Also available as `GetDeveloperProductsAsync`. Waits for the answer.

## Properties

- `ProcessConsumableReceipt: (receipt: table) -> Enum.ConsumableDecision | boolean` - write-only. The function that grants consumable purchases. Return `Enum.ConsumableDecision.Granted` to confirm a receipt. Anything else leaves it open and it is delivered again. Also available as `ProcessReceipt`. The receipt table has `PurchaseId`, `PlayerId`, `ConsumableId`, `ProductId` (the same as `ConsumableId`), `PlaceIdWherePurchased`, and `CurrencySpent`. Server `Script` only. See the [Consumables guide](../../guides/consumables.md).

## Signals

- `PromptPurchaseFinished(player: Player, itemId: number, purchased: boolean, result: string)` - fires once for every prompt. `result` is `purchased`, `cancelled`, `expired`, `owned`, `insufficient_funds`, `limited`, or `unavailable`;
- `PromptGamePassPurchaseFinished(player: Player, gamePassId: number, purchased: boolean, result: string)` - fires once for every gamepass prompt. `result` is `purchased`, `cancelled`, `expired`, `owned`, `insufficient_funds`, or `unavailable`.;
- `PromptConsumablePurchaseFinished(player: Player, consumableId: number, purchased: boolean, result: string)` - fires once for every consumable prompt. `result` is `purchased`, `cancelled`, `expired`, `insufficient_funds`, or `unavailable`. Also available as `PromptProductPurchaseFinished(userId: number, consumableId: number, purchased: boolean)`.
