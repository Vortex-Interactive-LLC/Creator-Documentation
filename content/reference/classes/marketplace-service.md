---
title: MarketplaceService
description: A server-only service for prompting item and gamepass purchases.
---

## Summary

Get the service with `game:GetService("MarketplaceService")`. It is only available in server scripts. See the [Prompting Purchases guide](../../guides/marketplace-purchases.md) and the [Gamepasses guide](../../guides/gamepasses.md).

### Example

```luau
local MarketplaceService = game:GetService("MarketplaceService")

MarketplaceService:PromptPurchase(player, 1234)
```

## Methods

- `PromptPurchase(player: Player, itemId: number)` - opens the purchase window for the player and returns immediately. `itemId` must be a whole number from 1 to 2147483647;
- `PlayerOwnsAsset(player: Player, itemId: number): boolean` - returns whether the player owns the item. Waits for the answer;
- `GetProductInfo(id: number, infoType: Enum.InfoType?): table` - describes a catalog item, returning `Name`, `AssetType`, `PriceInVolts`, `IsForSale`, `IsLimited`, and `Creator` (`Id`, `Name`). With `Enum.InfoType.GamePass` it describes a gamepass instead, returning `Name`, `Description`, `PriceInVolts`, `IsForSale`, `GameId`, and `Creator` (`Id`, `Name`, `CreatorType`). Raises an error if it does not exist. Waits for the answer;
- `PromptGamePassPurchase(player: Player, gamePassId: number)` - opens the purchase window for a gamepass and returns immediately;
- `UserOwnsGamePassAsync(user: Player | number, gamePassId: number): boolean` - returns whether the user owns the gamepass. `user` is a user id or a player. Waits for the answer.

## Signals

- `PromptPurchaseFinished(player: Player, itemId: number, purchased: boolean, result: string)` - fires once for every prompt. `result` is `purchased`, `cancelled`, `expired`, `owned`, `insufficient_funds`, `limited`, or `unavailable`;
- `PromptGamePassPurchaseFinished(player: Player, gamePassId: number, purchased: boolean, result: string)` - fires once for every gamepass prompt. `result` is `purchased`, `cancelled`, `expired`, `owned`, `insufficient_funds`, or `unavailable`.
