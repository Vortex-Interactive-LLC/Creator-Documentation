---
title: Sandbox Limits
description: Runtime boundaries verified in Vortex Studio.
---
> [!Summary]
> Sandbox limits define which globals and system APIs are unavailable inside Vortex scripts. These restrictions help keep scripts safe and predictable while you build gameplay logic.

## No dynamic code or filesystem access

In Vortex Studio 0.3.4, both Script and LocalScript have no `require`, `load`, `loadstring`, `loadfile`, `dofile`, `io`, `os`, `package`, `debug`, `bit32`, `buffer`, or `vector` global. The `shared` global is also absent.

Executor-style filesystem and hook globals are unavailable: `readfile`, `writefile`, `appendfile`, `listfiles`, `isfile`, `isfolder`, `makefolder`, `delfile`, `getgenv`, `getrenv`, `getgc`, and `hookfunction` all read as `nil`.

## No privileged game entry points

`game.HttpGet`, `game.HttpPost`, `game.GetObjects`, `game.Loaded`, and `Instance.fromExisting` are unavailable. `HttpService`, `DataStoreService`, `TeleportService`, `MarketplaceService`, and `InsertService` are not valid services in either execution context.

## Available reflection helpers

`_G` is a table. Lua reflection helpers including `getfenv`, `setfenv`, `getmetatable`, `setmetatable`, `rawget`, `rawset`, `rawequal`, `newproxy`, and `collectgarbage` are exposed.

Their presence does not establish access outside the Vortex runtime sandbox. Treat scripts as isolated from the filesystem, arbitrary code loading, external networking, and privileged Roblox services.
