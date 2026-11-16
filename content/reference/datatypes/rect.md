---
title: Rect
description: A rectangle made of a minimum and a maximum corner.
---

## Summary

A `Rect` is the type of [`ImageLabel`](../classes/image-label.md) properties that pick a region of an image in pixels. It holds two [`Vector2`](./vector2.md) corners.

```lua
local rect = Rect.new(10, 10, 50, 40)
print(rect.Width, rect.Height) -- 40 30
```

## Constructors

- `Rect.new(minX: number, minY: number, maxX: number, maxY: number)`;
- `Rect.new(min: Vector2, max: Vector2)`.

## Properties

- `Min`, `Max` - the top-left and bottom-right corners as [`Vector2`](./vector2.md);
- `Width`, `Height` - `Max` minus `Min` on each axis, read-only.

## Operators

`==` between two `Rect`s, and a `Lerp` method.
