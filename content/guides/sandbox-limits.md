---
title: Sandbox Limits
description: Runtime boundaries verified in Vortex Studio.
---
> [!Summary]
> Sandbox limits define which globals and system APIs are unavailable inside Vortex scripts. These restrictions help keep scripts safe and predictable while you build gameplay logic.

## No dynamic code or filesystem access

Both Script and LocalScript have no `load`, `loadstring`, `loadfile`, `dofile`, `io`, `package`, `debug`, `bit32`, `buffer`, `utf8`, or `vector` global. The `shared` global is also absent. `require` is available for loading ModuleScripts.

The `os` library only provides `os.time`, `os.clock`, `os.date`, and `os.difftime`.

Executor-style filesystem and hook globals are unavailable: `readfile`, `writefile`, `appendfile`, `listfiles`, `isfile`, `isfolder`, `makefolder`, `delfile`, `getgenv`, `getrenv`, `getgc`, and `hookfunction` all read as `nil`.

## No privileged game entry points

`game.HttpGet`, `game.HttpPost`, `game.GetObjects`, `game.Loaded`, and `Instance.fromExisting` are unavailable. `HttpService`, `TeleportService`, and `InsertService` are not valid services in either execution context. `DataStoreService` and `MarketplaceService` are valid, but only in server Scripts.

## Available reflection helpers

`_G` is a table. The Lua helpers `getmetatable`, `setmetatable`, `rawget`, `rawset`, `rawequal`, and `rawlen` are exposed. `getfenv`, `setfenv`, `newproxy`, and `collectgarbage` are not available.

Their presence does not establish access outside the Vortex runtime sandbox. Treat scripts as isolated from the filesystem, arbitrary code loading, external networking, and privileged Roblox services.
