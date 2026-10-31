---
title: TextChatService
description: A server-only service for showing chat bubbles.
---

## Summary

Get the service with `game:GetService("TextChatService")`. It is only available in server scripts.

### Example

```luau
local TextChatService = game:GetService("TextChatService")

TextChatService:DisplayBubble(workspace.Shopkeeper, "Welcome!")
```

## Methods

- `DisplayBubble(adornee: Part | Character, message: string)` - shows a chat bubble over `adornee` for every player and returns immediately. `message` is cut to 120 characters and filtered like chat, so a blocked message shows as `#` characters. If the filter cannot be reached, or the server is over its filter limit of 1000 requests a minute, no bubble is shown and a warning is printed. A bubble lasts about 12 seconds, and up to 3 show at a time.
