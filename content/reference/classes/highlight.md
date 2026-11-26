---
title: Highlight
description: Draws a colored fill and outline over a part or model.
---

## Summary

A `Highlight` tints and outlines the part or model it is attached to. By default that is its parent. Set `Adornee` to highlight something else.

```luau
local highlight = Instance.new("Highlight")
highlight.FillColor = Color3.fromRGB(255, 200, 0)
highlight.FillTransparency = 0.6
highlight.OutlineColor = Color3.new(1, 1, 1)
highlight.Parent = workspace.Statue
```

## Properties

- `Adornee` - the `Instance` to highlight. When `nil`, the parent is used;
- `Enabled` - `boolean`, defaults to `true`;
- `FillColor` - [`Color3`](../datatypes/color3.md), defaults to red;
- `FillTransparency` - `number` from `0` to `1`. Defaults to `0.5`;
- `OutlineColor` - [`Color3`](../datatypes/color3.md), defaults to white;
- `OutlineTransparency` - `number` from `0` to `1`. Defaults to `0`;
- `DepthMode` - `Enum.HighlightDepthMode`. `AlwaysOnTop` shows the highlight through walls and is the default. `Occluded` hides it behind other parts;
- `Name`, `ClassName`, `Parent`.

## Notes

- A model highlights up to 64 of its parts;
- Wedges and mesh parts are highlighted as their bounding box;
- Parts added to a highlighted model later are not picked up until a `Highlight` property changes;
- The outline is drawn around each part, so touching parts of a model show outlines between them.
