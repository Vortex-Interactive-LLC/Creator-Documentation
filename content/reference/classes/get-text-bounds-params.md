---
title: GetTextBoundsParams
description: Settings for TextService:GetTextBoundsAsync.
---

## Summary

Create one with `Instance.new("GetTextBoundsParams")`, set the properties, and pass it to [`TextService:GetTextBoundsAsync`](./text-service.md). It cannot be parented to anything.

### Example

```luau
local TextService = game:GetService("TextService")

local params = Instance.new("GetTextBoundsParams")
params.Text = "Hello world"
params.Font = Font.fromEnum(Enum.Font.Fredoka)
params.Size = 24
params.Width = 200

local size = TextService:GetTextBoundsAsync(params)
```

## Properties

- `Text: string` - the text to measure. Defaults to an empty string;
- `Font: Font` - the font to measure with. Defaults to the first bundled font;
- `Size: number` - the text size. Defaults to `14`;
- `Width: number` - the width the text wraps at. Defaults to `math.huge`, which means no wrapping;
- `RichText: boolean` - when `true`, tags such as `<b>` are removed before measuring. Defaults to `false`. Text labels do not draw rich text yet, so this only affects the measurement.
