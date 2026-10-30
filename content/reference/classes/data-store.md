---
title: DataStore
description: A named store of values that persist between servers.
---

## Summary

Returned by [`DataStoreService:GetDataStore`](./data-store-service.md). See the [DataStores guide](../../guides/datastores.md).

## Properties

- `Name` - the store name;
- `ClassName` - `"DataStore"`.

## Methods

- `GetAsync(key: string): (any, DataStoreKeyInfo)` - returns the saved value and its [`DataStoreKeyInfo`](../datatypes/data-store-key-info.md), or `nil` for a key that was never saved;
- `SetAsync(key: string, value: any): string` - saves the value and returns its version;
- `UpdateAsync(key: string, transform: (old: any, info: DataStoreKeyInfo) -> any): (any, DataStoreKeyInfo)` - reads the key, passes the value to `transform`, and saves the result. Returning `nil` cancels the update. `transform` cannot yield;
- `IncrementAsync(key: string, delta: number?): number` - adds `delta` (default `1`) to a number and returns the result. A missing key starts at `0`;
- `RemoveAsync(key: string): any` - deletes the key and returns the value it held.

Keys are 1 to 50 characters, and values can be numbers, strings, booleans and tables of those up to 4 MB. All methods wait for the result and raise an error with a numeric code on failure.
