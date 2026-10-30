---
title: SurfaceGui
description: A GUI drawn on a face of a part.
---

## Summary

A `SurfaceGui` inside a `Part` draws its contents on one face of that part.

## Properties

- `Face` - `Enum.NormalId`: `Right`, `Top`, `Back`, `Left`, `Bottom` or `Front`. Defaults to `Front`;
- `PixelsPerStud` - `number`, the resolution of the surface. Defaults to `50`;
- `MaxDistance` - `number`, the furthest distance it is shown from. `0` means the default limit of 600 studs;
- `AlwaysOnTop` - `boolean`, defaults to `false`;
- `Active` - `boolean`, defaults to `true`;
- `Enabled` - `boolean`, defaults to `true`;
- `Name`, `ClassName`, `Parent`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave` and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
