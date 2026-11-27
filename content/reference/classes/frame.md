---
title: Frame
description: A rectangle used to group and lay out other GUI objects.
---

## Summary

A `Frame` is a box. Use it to group other objects, as a background, or as a panel. It must be inside a [`ScreenGui`](./screen-gui.md), a [`BillboardGui`](./billboard-gui.md), a [`SurfaceGui`](./surface-gui.md), or another GUI object. See [Building GUIs](../../guides/gui.md).

### Example

```luau
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0.5, 0, 0, 100)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.Parent = screenGui
```

## Properties

- `Position` - [`UDim2`](../datatypes/udim2.md), defaults to `0, 0, 0, 0`;
- `Size` - [`UDim2`](../datatypes/udim2.md), default `0, 100, 0, 100`;
- `AnchorPoint` - [`Vector2`](../datatypes/vector2.md), the point of the object that `Position` refers to. Defaults to `0, 0`;
- `Rotation` - `number`, in degrees clockwise, defaults to `0`. The object turns around its centre, and everything inside it turns with it. A child's `Rotation` adds to its parent's. Backgrounds, strokes, images, text and gradients all turn with the object. `AnchorPoint` does not move the pivot, and `AbsolutePosition` and `AbsoluteSize` stay the values from before rotating. See [Rotating](#rotating);
- `Visible` - `boolean`, defaults to `true`. When `false` the object and everything inside it is hidden;
- `ZIndex` - `number`, draw order among siblings. Defaults to `1`;
- `LayoutOrder` - `number`, order inside a `UIListLayout`. Defaults to `0`;
- `BackgroundColor3` - [`Color3`](../datatypes/color3.md), defaults to `1, 1, 1`;
- `BackgroundTransparency` - `number`, defaults to `0`;
- `BorderSizePixel` - `number`, the width in pixels of a border drawn around the object, outside its edges and above its `UICorner` shape. Defaults to `0`. A `UIStroke` on the object replaces it;
- `BorderColor3` - [`Color3`](../datatypes/color3.md), defaults to `0.11, 0.16, 0.21`;
- `ClipsDescendants` - `boolean`, defaults to `false`;
- `AutomaticSize` - `Enum.AutomaticSize`: `None`, `X`, `Y`, or `XY`. On the chosen axes the object grows to fit its children, and `Size` becomes the minimum. Children are measured from the object's top-left corner, including the right and bottom `UIPadding` and any `UIListLayout` or `UIGridLayout`. Children sized by `Scale` are measured against that minimum, so avoid full-scale children on an automatic axis. On a text object it fits the text, wrapping at the object's width when `TextWrapped` is set and that axis is not automatic, and adds any `UIPadding`; it does not fit `TextScaled` text. Does not apply to a [`ScrollingFrame`](./scrolling-frame.md), which has `AutomaticCanvasSize`. Defaults to `None`;
- `Active` - `boolean`, whether the object receives input. Defaults to `false`;
- `AbsolutePosition` - [`Vector2`](../datatypes/vector2.md), read-only. The top-left corner in pixels, relative to the top-left of the game view. `0, 0` while the object is hidden or not yet laid out;
- `AbsoluteSize` - [`Vector2`](../datatypes/vector2.md), read-only. The size in pixels after `Size`, `UIListLayout` and `UIPadding` are applied;
- `AbsoluteRotation` - `number`, read-only. Its own `Rotation` plus the `Rotation` of every parent above it, in degrees. `0` while the object is hidden or not yet laid out;
- `Name`, `ClassName`, `Parent`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, `Activated`, and the pointer signals `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`. The pointer signals fire for every visible object under the pointer. The others only fire for objects that receive input: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).

## Rotating

- A rotated object clips its children to the smallest upright rectangle that holds its turned area, so a corner of a tilted `ClipsDescendants` frame can show a little extra;
- Edges of a rotated `Tile` or `Slice` image are not smoothed. Other rotated shapes are;
- Clicks, hovering and scrolling follow the turned shape, so a tilted button responds where it is drawn and not in the box it had before turning;
- A [`TextBox`](./text-box.md) that is rotated, or inside a rotated object, draws its text turned but cannot be clicked into for typing. Keep text boxes upright.
