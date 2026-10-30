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
- `Visible` - `boolean`, defaults to `true`. When `false` the object and everything inside it is hidden;
- `ZIndex` - `number`, draw order among siblings. Defaults to `1`;
- `LayoutOrder` - `number`, order inside a `UIListLayout`. Defaults to `0`;
- `BackgroundColor3` - [`Color3`](../datatypes/color3.md), defaults to `1, 1, 1`;
- `BackgroundTransparency` - `number`, defaults to `0`;
- `ClipsDescendants` - `boolean`, defaults to `false`;
- `Active` - `boolean`, whether the object receives input. Defaults to `false`;
- `Name`, `ClassName`, `Parent`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave` and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
