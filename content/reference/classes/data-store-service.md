---
title: DataStoreService
description: A server-only service that provides persistent data stores.
---

## Summary

Get the service with `game:GetService("DataStoreService")`. It is only available in server scripts; a `LocalScript` raises an error. See the [DataStores guide](../../guides/datastores.md).

### Example

```luau
local DataStoreService = game:GetService("DataStoreService")
local store = DataStoreService:GetDataStore("PlayerData")
```

## Methods

- `GetDataStore(name: string, scope: string?): DataStore` - returns the store with that name and scope. `scope` defaults to `"global"`. Both must be 1 to 50 characters;
- `GetOrderedDataStore(name: string, scope: string?): OrderedDataStore` - returns an [ordered store](./ordered-data-store.md);
- `GetRequestBudgetForRequestType(requestType: Enum.DataStoreRequestType): number` - returns how many requests of that kind can be made right now.

Asking for the same name and scope again returns the same object.
