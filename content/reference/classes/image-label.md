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
- `ScaleType` - `Enum.ScaleType`: `Stretch` fills the box, `Fit` keeps the aspect ratio and centres the image, `Crop` fills the box and trims the image. Defaults to `Stretch`;
- every property of a [`Frame`](./frame.md).

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
