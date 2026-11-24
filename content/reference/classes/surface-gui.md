---
title: SurfaceGui
description: A GUI drawn on a face of a part.
---

## Summary

A `SurfaceGui` inside a `Part` draws its contents on one face of that part.

## Properties

- `Face` - `Enum.NormalId`: `Right`, `Top`, `Back`, `Left`, `Bottom`, or `Front`. Defaults to `Front`;
- `Adornee` - [`Instance`](./instance.md) | `nil`, the part the GUI is drawn on. When `nil`, the part the `SurfaceGui` is inside is used;
- `SizingMode` - `Enum.SurfaceGuiSizingMode`: `FixedSize` gives the GUI a canvas of `CanvasSize` pixels, and `PixelsPerStud` makes the canvas as big as the face is at `PixelsPerStud`. Defaults to `FixedSize`;
- `CanvasSize` - [`Vector2`](../datatypes/vector2.md), the size of the canvas in pixels when `SizingMode` is `FixedSize`. Each side is clamped between `1` and `4096`. Defaults to `800, 600`;
- `PixelsPerStud` - `number`, the resolution of the surface when `SizingMode` is `PixelsPerStud`. Defaults to `50`;
- `LightInfluence` - `number` from `0` to `1`, how much the lighting of the world affects the colours of the GUI. Defaults to `0`;
- `Brightness` - `number` from `0` to `1000`, multiplies the brightness of the GUI. Defaults to `1`;
- `ZOffset` - `number`, moves the GUI toward or away from the camera, in studs, to decide which of two overlapping surfaces is drawn on top. Defaults to `0`;
- `ClipsDescendants` - `boolean`, defaults to `false`. When `true`, anything outside the canvas is cut off;
- `ToolPunchThroughDistance` - `number`, defaults to `0`;
- `ZIndexBehavior` - `Enum.ZIndexBehavior`, defaults to `Global`. `Global` compares the `ZIndex` of every object in the GUI, and `Sibling` only compares objects with the same parent;
- `ResetOnSpawn` - `boolean`, defaults to `true`;
- `MaxDistance` - `number`, the furthest distance it is shown from. `0` means the default limit of 600 studs;
- `AlwaysOnTop` - `boolean`, defaults to `false`;
- `Active` - `boolean`, defaults to `true`;
- `Enabled` - `boolean`, defaults to `true`;
- `Name`, `ClassName`, `Parent`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, `Activated`, and the pointer signals `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`. The pointer signals fire for every visible object under the pointer. The others only fire for objects that receive input: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
