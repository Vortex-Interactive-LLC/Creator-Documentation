---
title: ContentProvider
description: Waits for assets to be ready before you use them.
---

## Summary

Get the service with `game:GetService("ContentProvider")`. It is available in server and client scripts.

### Example

```luau
local ContentProvider = game:GetService("ContentProvider")

local sounds = {}
for _, child in workspace.Sounds:GetChildren() do
    if child:IsA("Sound") then
        table.insert(sounds, child)
    end
end

ContentProvider:PreloadAsync(sounds, function(contentId, status)
    print(contentId, status)
end)
print("ready")
```

## Properties

- `RequestQueueSize` - `number`, always `0`;
- `Name` - `"ContentProvider"`;
- `ClassName` - `"ContentProvider"`.

## Methods

- `PreloadAsync(assets: {any}, callback: ((contentId: string, status: Enum.AssetFetchStatus) -> ())?)` - waits until every [`Sound`](./sound.md) in `assets` has its length loaded, or for up to 10 seconds. Other items are treated as already loaded. If `callback` is given, it is called once per item with its id and `Enum.AssetFetchStatus.Success`, or `Enum.AssetFetchStatus.TimedOut` if the sound did not load in time. A sound that is not approved yet, and does not belong to you, never loads.
