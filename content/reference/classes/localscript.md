---
title: LocalScript
description: A script that runs locally for a client.
---

## Summary

A LocalScript runs on the client (the player's machine). Use LocalScripts for client-only behavior such as UI, camera control, and input handling; do not use them for server-authoritative logic.

## Typical properties and methods

- `Parent` : Instance — where the script is placed (e.g., PlayerGui or StarterPlayerScripts).
- `Disabled` : Boolean — whether the script is currently disabled.
- `Source` : string — the script source (editor-only or read-only in some tools; not guaranteed to be available at runtime).

## Example

```luau
-- Example LocalScript that prints the local player's name
local Players = game:GetService("Players")
local player = Players.LocalPlayer
if player then
  print("Hello, " .. player.Name)
end
```

## Notes

- `Players.LocalPlayer` is only available in client or LocalScript contexts; it will be nil in server scripts.
- LocalScripts do not run in server-only containers such as `ServerScriptService`.
- Avoid trusting client-side code for security, permissions, or authoritative game state — always verify on the server.
- Good places for LocalScripts include: `StarterPlayerScripts`, `StarterGui`/`PlayerGui`, `StarterCharacterScripts`, `Backpack` (for tool-local behavior).
