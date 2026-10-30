---
title: BillboardGui
description: A GUI that floats above a part in the world.
---

## Summary

A `BillboardGui` inside a `Part`, or a `Model`, draws its contents at that object in the world.

## Properties

- `Size` - [`UDim2`](../datatypes/udim2.md), defaults to `0, 200, 0, 50`;
- `StudsOffset` - [`Vector3`](../datatypes/vector3.md), moves the GUI from the part, in studs. Defaults to `0, 0, 0`;
- `MaxDistance` - `number`, the furthest distance it is shown from. `0` means no limit. Defaults to `0`;
- `AlwaysOnTop` - `boolean`, draw it over other objects. Defaults to `false`;
- `Active` - `boolean`, defaults to `true`;
- `Enabled` - `boolean`, defaults to `true`;
- `Name`, `ClassName`, `Parent`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
