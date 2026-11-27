---
title: CanvasGroup
description: A frame that fades itself and everything inside it with one property.
---

## Summary

A `CanvasGroup` is a [`Frame`](./frame.md) with one extra property, `GroupTransparency`. Setting it fades the group's background, its images, its text, its strokes and every object inside it together, which is how you fade a whole menu in or out with a single [`Tween`](./tween-service.md). See [Building GUIs](../../guides/gui.md).

### Example

```luau
local TweenService = game:GetService("TweenService")

local menu = Instance.new("CanvasGroup")
menu.Size = UDim2.new(0, 300, 0, 200)
menu.GroupTransparency = 1
menu.Parent = screenGui

TweenService:Create(menu, TweenInfo.new(0.4), {GroupTransparency = 0}):Play()
```

## Properties

- `GroupTransparency` - `number` from `0` to `1`, defaults to `0`. `0` shows the group normally and `1` hides all of it. It stacks with the group's own `BackgroundTransparency`, with `GroupTransparency` of any `CanvasGroup` it sits inside, and with each child's own transparency;
- everything a [`Frame`](./frame.md) has, including `Position`, `Size`, `Rotation`, `ClipsDescendants`, `AutomaticSize`, the `Absolute` properties and the input signals;
- `Name`, `ClassName`, `Parent`.

## Limits

- Each object inside the group is faded on its own, not flattened into one layer first. Where two translucent children overlap, the one underneath still shows through the one on top. A group whose children do not overlap fades the same as it would if flattened;
- A faded object still receives clicks, so set `Visible` to `false` or `Active` to `false` once a menu has faded out.
