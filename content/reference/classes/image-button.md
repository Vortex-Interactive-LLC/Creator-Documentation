---
title: ImageButton
description: A clickable GUI object that displays an image.
---

## Summary

An `ImageButton` is an [`ImageLabel`](./image-label.md) that receives input. It always fires the mouse signals and darkens while the mouse is over it unless `AutoButtonColor` is `false`.

## Properties

- `AutoButtonColor` - `boolean`, darkens the button while the mouse is over it and while it is pressed. Defaults to `true`;
- every property of an [`ImageLabel`](./image-label.md).

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, and `Activated`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
