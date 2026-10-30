---
title: DataStoreKeyInfo
description: Information about the saved version of a data store key.
---

## Summary

Returned as the second value of [`DataStore:GetAsync`](../classes/data-store.md), and passed to the `UpdateAsync` callback.

## Properties

- `Version` - `string`, the version of the saved value. It is the same string `SetAsync` returned when the value was saved;
- `CreatedTime` - `number`, when the key was first saved;
- `UpdatedTime` - `number`, when it was last saved.

## Methods

- `GetUserIds(): { number }` - returns an empty table;
- `GetMetadata(): { [string]: any }` - returns an empty table.
