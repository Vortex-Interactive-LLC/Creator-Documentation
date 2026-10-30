---
title: UDim2
description: A two-dimensional size or position made of scale and pixel offset values.
---

## Summary

A `UDim2` is the type of GUI `Size` and `Position`. Each axis is a [`UDim`](./udim.md): a fraction of the parent plus a number of pixels.

```lua
frame.Size = UDim2.new(0.5, 0, 0, 100) -- half the parent's width, 100 pixels tall
frame.Position = UDim2.fromScale(0.5, 0.5)
```

## Constructors

- `UDim2.new(xScale: number, xOffset: number, yScale: number, yOffset: number)`;
- `UDim2.fromScale(xScale: number, yScale: number)` - offsets are `0`;
- `UDim2.fromOffset(xOffset: number, yOffset: number)` - scales are `0`.

## Properties

- `X`, `Y` - the [`UDim`](./udim.md) for each axis;
- `Width`, `Height` - the same values as `X` and `Y`.

## Operators

`+`, `-`, and `==` between two `UDim2`s, and a `Lerp` method.
