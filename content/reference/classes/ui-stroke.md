---
title: UIStroke
description: Draws an outline around the GUI object it is inside.
---

## Summary

Place a `UIStroke` inside a GUI object to outline it. On a text object it outlines the text. A fully transparent frame draws nothing, but its stroke is still drawn.

## Properties

- `Thickness` - `number`, defaults to `1`;
- `Color` - [`Color3`](../datatypes/color3.md), defaults to `0, 0, 0`;
- `Transparency` - `number`, defaults to `0`;
- `ApplyStrokeMode` - `Enum.ApplyStrokeMode`: `Contextual` or `Border`. Defaults to `Contextual`;
- `Name`, `ClassName`, `Parent`.
