---
title: MarketplaceService
description: A server-only service for prompting item purchases.
---

## Summary

Get the service with `game:GetService("MarketplaceService")`. It is only available in server scripts. See the [Prompting Purchases guide](../../guides/marketplace-purchases.md).

### Example

```luau
local MarketplaceService = game:GetService("MarketplaceService")

MarketplaceService:PromptPurchase(player, 1234)
```

## Methods

- `PromptPurchase(player: Player, itemId: number)` - opens the purchase window for the player and returns immediately. `itemId` must be a whole number from 1 to 2147483647;
- `PlayerOwnsAsset(player: Player, itemId: number): boolean` - returns whether the player owns the item. Waits for the answer;
- `GetProductInfo(itemId: number): table` - returns `Name`, `AssetType`, `PriceInVolts`, `IsForSale`, `IsLimited` and `Creator` (`Id`, `Name`). Raises an error if the item does not exist. Waits for the answer.

## Signals

- `PromptPurchaseFinished(player: Player, itemId: number, purchased: boolean, result: string)` - fires once for every prompt. `result` is `purchased`, `cancelled`, `expired`, `owned`, `insufficient_funds`, `limited` or `unavailable`.
