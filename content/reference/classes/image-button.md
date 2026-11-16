---
title: ImageButton
description: A clickable GUI object that displays an image.
---

## Summary

An `ImageButton` is an [`ImageLabel`](./image-label.md) that receives input. It always fires the mouse signals and darkens while the mouse is over it unless `AutoButtonColor` is `false`.

## Properties

- `AutoButtonColor` - `boolean`, darkens the button while the mouse is over it and while it is pressed. While a `HoverImage` or `PressedImage` is showing, the button is not darkened. Defaults to `true`;
- `HoverImage` - `number`, an image id shown instead of `Image` while the mouse is over the button. Defaults to `0`, which keeps showing `Image`;
- `PressedImage` - `number`, an image id shown instead of `Image` while the button is held down. Defaults to `0`, which keeps showing `Image`, also when `HoverImage` is set. Both images use the button's `ScaleType`, `ImageRectOffset`, `ImageRectSize`, `SliceCenter` and `ImageColor3`. An image that has not loaded yet is skipped and `Image` shows instead;
- every property of an [`ImageLabel`](./image-label.md).

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, `Activated`, and the pointer signals `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
