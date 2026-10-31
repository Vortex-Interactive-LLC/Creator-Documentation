---
title: TextService
description: Filters text shown to players and measures text.
---

## Summary

Get the service with `game:GetService("TextService")`. Text on screen is not filtered for you: run any text you did not write yourself (player input, data store values, names) through `FilterStringAsync` before showing it. Chat is filtered automatically.

### Example

```luau
local TextService = game:GetService("TextService")

local ok, result = pcall(function()
    return TextService:FilterStringAsync(name, player.UserId)
end)
if ok then
    label.Text = result:GetNonChatStringForBroadcastAsync()
end
```

## Methods

- `FilterStringAsync(text: string, fromUserId: number, context: Enum.TextFilterContext?): TextFilterResult` - filters `text` written by `fromUserId`. Waits for the answer. Server scripts only. `text` can be at most 512 characters and `context` has no effect yet. Raises an error if the filter cannot be reached or the server sends more than 1000 requests in a minute, so use `pcall`. Nothing is blocked in Studio;
- `GetTextSize(text: string, fontSize: number, font: Enum.Font, frameSize: Vector2): Vector2` - the size in pixels the text takes up. It wraps at `frameSize.X`; `frameSize.Y` is ignored. Only the first 2000 characters are measured. LocalScripts only;
- `GetTextBoundsAsync(params: GetTextBoundsParams): Vector2` - same, with the settings in a [GetTextBoundsParams](./get-text-bounds-params.md). LocalScripts only;
- `GetFamilyInfoAsync(family: string): table` - returns `Name` and `Faces` (each with `Name`, `Weight`, `Style`) for a bundled font. Raises an error for an unknown family;
- `GetTextSizeOffsetAsync(fontSize: number, font: Font): number` - always returns `0`.
