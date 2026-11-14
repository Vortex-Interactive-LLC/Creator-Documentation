---
title: ScrollingFrame
description: A frame whose contents can be scrolled with the mouse wheel or its scroll bar.
---

## Summary

A `ScrollingFrame` is a [`Frame`](./frame.md) with a canvas larger than the frame itself. Children are positioned inside the canvas, and the frame shows a window onto it. It always clips its children to that window, and it draws a scroll bar when the canvas overflows.

```luau
local list = Instance.new("ScrollingFrame")
list.Size = UDim2.new(0, 240, 0, 300)
list.AutomaticCanvasSize = Enum.AutomaticCanvasSize.Y
list.CanvasSize = UDim2.new()
list.Parent = screenGui

local layout = Instance.new("UIListLayout")
layout.Padding = UDim.new(0, 6)
layout.Parent = list
```

Scale values in a child's `Position` and `Size` are a fraction of the canvas, not of the frame. Scale values in `CanvasSize` are a fraction of the frame's window, which is the frame minus the scroll bar.

## Properties

- `CanvasSize` - [`UDim2`](../datatypes/udim2.md), defaults to `0, 0, 2, 0`. The canvas never shrinks below the window;
- `CanvasPosition` - [`Vector2`](../datatypes/vector2.md), the scroll offset in pixels. Values outside the scrollable range are clamped, so `Vector2.new(0, 1e6)` scrolls to the bottom;
- `AutomaticCanvasSize` - `None` (default), `X`, `Y` or `XY`. On an automatic axis the canvas fits its children, including any `UIPadding`, and `CanvasSize` is ignored on that axis;
- `ScrollingDirection` - `X`, `Y` or `XY` (default). Limits what the wheel and scroll bar can do. A script can still set `CanvasPosition` on any axis;
- `ScrollingEnabled` - `boolean`, defaults to `true`. When `false` the wheel and scroll bar do nothing;
- `ScrollBarThickness` - `number`, defaults to `12`. Set it to `0` to hide the scroll bar;
- `ScrollBarImageColor3` - [`Color3`](../datatypes/color3.md), defaults to black;
- `ScrollBarImageTransparency` - `number`, defaults to `0`;
- `AbsoluteCanvasSize` - [`Vector2`](../datatypes/vector2.md), read-only. The size of the canvas in pixels, including automatic sizing;
- `AbsoluteWindowSize` - [`Vector2`](../datatypes/vector2.md), read-only. The visible area in pixels, which is the frame minus the scroll bar;
- everything a [`Frame`](./frame.md) has, such as `Position`, `Size`, `BackgroundColor3` and `Visible`.

## Notes

- The mouse wheel scrolls the innermost `ScrollingFrame` under the cursor, and the camera does not zoom while the cursor is over one.
- A scroll frame does not block clicks on what is behind it unless `Active` is `true`.
- To keep a chat log pinned to the bottom, set `CanvasPosition = Vector2.new(0, 1e6)` after adding a message. It is clamped to the bottom once the canvas has been laid out.
- The `Absolute` properties update after layout runs, so they can lag by one frame right after you change a size or add a child.
