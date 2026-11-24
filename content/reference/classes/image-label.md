---
title: ImageLabel
description: A GUI object that displays an image.
---

## Summary

An `ImageLabel` is a box that draws an image. It draws nothing until `Image` is set.

## Properties

- `Image` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md). Defaults to `0`, which draws nothing;
- `ImageColor3` - [`Color3`](../datatypes/color3.md), tints the image. Defaults to `1, 1, 1`;
- `ImageTransparency` - `number`, defaults to `0`;
- `ScaleType` - `Enum.ScaleType`: `Stretch` fills the box, `Fit` keeps the aspect ratio and centres the image, `Crop` fills the box and trims the image, `Tile` repeats the image across the box, `Slice` stretches the middle and edges of the image while keeping its corners at their original size. Defaults to `Stretch`;
- `ResampleMode` - `Enum.ResamplerMode`: `Default` smooths the image when it is scaled, and `Pixelated` keeps hard pixel edges, which suits pixel art. Defaults to `Default`;
- `ImageRectOffset` - [`Vector2`](../datatypes/vector2.md), the top-left corner in pixels of the part of the image to draw. Defaults to `0, 0`;
- `ImageRectSize` - [`Vector2`](../datatypes/vector2.md), the size in pixels of that part. `0, 0` draws the whole image, which is the default. The part is clamped to the image, and `ScaleType` applies to it instead of the whole image;
- `TileSize` - [`UDim2`](../datatypes/udim2.md), the size of one repeat when `ScaleType` is `Tile`. The scale part is a fraction of the box. Defaults to `1, 0, 1, 0`, one repeat the size of the box. Tiles that would number more than 4096, or are smaller than a pixel, are drawn as `Stretch`. `Tile` ignores `UICorner`;
- `SliceCenter` - [`Rect`](../datatypes/rect.md), the stretchable middle of the image in pixels, used when `ScaleType` is `Slice`. Everything outside it is a corner or an edge. A `Rect` with no area, which is the default, draws as `Stretch`. It is measured within `ImageRectOffset` and `ImageRectSize` when those are set;
- `SliceScale` - `number`, multiplies the size of the corners and edges, so a `2` draws a border twice as thick. Defaults to `1`. Corners shrink together when the box is too small to fit them. `Slice` ignores `UICorner`;
- every property of a [`Frame`](./frame.md).

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, `Activated`, and the pointer signals `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`. The pointer signals fire for every visible object under the pointer. The others only fire for objects that receive input: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
