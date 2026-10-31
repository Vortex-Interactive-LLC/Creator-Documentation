---
title: TextFilterResult
description: The result of TextService:FilterStringAsync.
---

## Summary

Returned by [`TextService:FilterStringAsync`](./text-service.md). Show the text from one of its methods, never the original string.

## Methods

- `GetNonChatStringForBroadcastAsync(): string` - the filtered text for something every player sees;
- `GetNonChatStringForUserAsync(toUserId: number): string` - the filtered text for one player;
- `GetChatForUserAsync(toUserId: number): string` - the filtered text for a chat message to one player.

All three return the same text. If any of it is blocked, the whole string becomes `#` characters.
