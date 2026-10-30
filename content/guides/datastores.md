---
title: DataStores
description: Save and load player data that persists between servers and sessions.
---
[`DataStoreService`](../reference/classes/data-store-service.md) saves data that lives beyond a single server, such as a player's coins or inventory. It is only available in server scripts. Calling `game:GetService("DataStoreService")` from a `LocalScript` raises an error.

```luau
-- Script
local Players = game:GetService("Players")
local DataStoreService = game:GetService("DataStoreService")

local store = DataStoreService:GetDataStore("PlayerData")

Players.PlayerAdded:Connect(function(player)
    local saved = store:GetAsync("player_" .. player.UserId)
    print(player.Name, "has", saved and saved.coins or 0, "coins")
end)

Players.PlayerRemoving:Connect(function(player)
    store:SetAsync("player_" .. player.UserId, { coins = 100 })
end)
```

The `*Async` methods wait for the result, so they pause the script that calls them. Other scripts keep running.

## Getting a store

`DataStoreService:GetDataStore(name, scope)` returns a [`DataStore`](../reference/classes/data-store.md). `scope` is optional and defaults to `"global"`. Stores with different names or scopes are completely separate, and asking for the same name and scope twice returns the same object.

## Reading and writing

```luau
local store = DataStoreService:GetDataStore("Example")

local version = store:SetAsync("key", { coins = 10, items = { "sword", "shield" } })
local value, info = store:GetAsync("key")
local old = store:RemoveAsync("key")
```

- `GetAsync(key)` returns the value and a [`DataStoreKeyInfo`](../reference/datatypes/data-store-key-info.md). A key that was never saved returns `nil`.
- `SetAsync(key, value)` saves the value and returns the new version string.
- `RemoveAsync(key)` deletes the key and returns the value it held.
- `IncrementAsync(key, delta)` adds to a number and returns the result. `delta` defaults to `1`, and a missing key starts from `0`.

A key is a string of 1 to 50 characters. A number is also accepted and converted to a string, so `12345` and `"12345"` are the same key.

## Updating safely

`UpdateAsync` reads the current value, passes it to your function, and saves what you return. If another server changed the key in the meantime, it retries with the newer value, so two servers cannot overwrite each other's changes.

```luau
store:UpdateAsync("Coins", function(old)
    return (old or 0) + 10
end)
```

Return `nil` from the function to cancel the update. The function must not yield, so do not call `task.wait` inside it.

## What can be stored

Numbers, strings, booleans, and tables of those can be stored, including nested tables. Instances, functions, `Vector3` and other datatypes cannot. Convert them to plain numbers and strings first. A value can be at most 4 MB, and `nil` is not a valid value to save. Use `RemoveAsync` instead.

## Errors

Failures raise an error whose message starts with a numeric code. Wrap calls in `pcall` so one failed save does not stop your script.

```luau
local ok, result = pcall(function()
    return store:GetAsync("key")
end)

if not ok then
    warn("DataStore failed:", result)
end
```

| Code | Meaning |
| --- | --- |
| `101` | The key is empty. |
| `102` | The key is longer than 50 characters. |
| `103` | The value is not valid for this store. |
| `104` | The value contains something that cannot be stored. |
| `105` | The value is larger than 4 MB. |
| `301` | The request was throttled. |
| `512` | The game is over its storage quota. |

## Request limits

Each kind of request has a budget that refills over time and grows with the number of players. A `GetAsync`, `SetAsync`, `IncrementAsync`, `RemoveAsync` or `UpdateAsync` budget starts at 60 requests per minute plus 10 per player. Ordered store sorted reads and writes have smaller budgets. Check what is left with:

```luau
local left = DataStoreService:GetRequestBudgetForRequestType(Enum.DataStoreRequestType.GetAsync)
```

Writing the same key more than once every 6 seconds queues the later writes instead of sending them straight away, and reading a key you just read within about 4 seconds returns the cached value. Save when a player leaves rather than on every change.

## Saving when the server closes

When a server shuts down, `PlayerRemoving` fires for the remaining players, and functions registered with `game:BindToClose` run first and are given time to finish.

```luau
game:BindToClose(function()
    for _, player in Players:GetPlayers() do
        store:SetAsync("player_" .. player.UserId, { coins = 100 })
    end
end)
```

## Ordered stores

An [`OrderedDataStore`](../reference/classes/ordered-data-store.md) keeps integer values and can return them sorted, which makes it the tool for leaderboards.

```luau
local scores = DataStoreService:GetOrderedDataStore("TopScores")
scores:SetAsync("player_1", 250)

local pages = scores:GetSortedAsync(false, 10)
for _, entry in pages:GetCurrentPage() do
    print(entry.key, entry.value)
end
```

`GetSortedAsync(ascending, pageSize, minValue, maxValue)` returns a [`DataStorePages`](../reference/datatypes/data-store-pages.md). `pageSize` is 1 to 100, and `minValue` and `maxValue` are optional and limit the range.

> [!NOTE]
> In Vortex Studio playtests, data is saved to a file on your computer instead of the live store. Use the Clear Data button in the Test group to reset it.
