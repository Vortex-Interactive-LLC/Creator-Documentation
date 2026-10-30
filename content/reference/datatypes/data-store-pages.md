---
title: DataStorePages
description: A sorted list of data store entries, read one page at a time.
---

## Summary

Returned by [`OrderedDataStore:GetSortedAsync`](../classes/ordered-data-store.md).

### Example

```luau
local pages = store:GetSortedAsync(false, 5)

while true do
    for _, entry in pages:GetCurrentPage() do
        print(entry.key, entry.value)
    end

    if pages.IsFinished then
        break
    end
    pages:AdvanceToNextPageAsync()
end
```

## Properties

- `IsFinished` - `boolean`, `true` when there are no more pages after the current one.

## Methods

- `GetCurrentPage(): { { key: string, value: number } }` - returns the entries on the current page;
- `AdvanceToNextPageAsync()` - loads the next page. It does nothing once `IsFinished` is `true`.
