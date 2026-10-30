---
title: OrderedDataStore
description: A data store of integers that can be read in sorted order.
---

## Summary

Returned by [`DataStoreService:GetOrderedDataStore`](./data-store-service.md). It works like a [`DataStore`](./data-store.md), except every value must be an integer and the store can be read in order. See the [DataStores guide](../../guides/datastores.md).

### Example

```luau
local scores = game:GetService("DataStoreService"):GetOrderedDataStore("TopScores")
scores:SetAsync("player_1", 250)

for _, entry in scores:GetSortedAsync(false, 10):GetCurrentPage() do
    print(entry.key, entry.value)
end
```

## Properties

- `Name` - the store name;
- `ClassName` - `"OrderedDataStore"`.

## Methods

- `GetAsync`, `SetAsync`, `UpdateAsync`, `IncrementAsync`, `RemoveAsync` - as on `DataStore`. `GetAsync` returns only the value, and values that are not integers raise an error;
- `GetSortedAsync(ascending: boolean, pageSize: number, minValue: number?, maxValue: number?): DataStorePages` - returns the entries in sorted order, `pageSize` (1 to 100) at a time. `minValue` and `maxValue` limit the range.
