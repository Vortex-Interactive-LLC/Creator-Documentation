---
title: UIGradient
description: Blends the colour and transparency of the GUI object it is inside along a line.
---

## Summary

Place a `UIGradient` inside a frame, button or image to colour it with a [`ColorSequence`](../datatypes/color-sequence.md) and fade it with a [`NumberSequence`](../datatypes/number-sequence.md). The gradient is multiplied with the colour the object already has: `BackgroundColor3` for the background and `ImageColor3` for an image. A transparency from the gradient stacks with the object's own, so a half-transparent frame under a half-transparent gradient is three quarters transparent. Rounded corners from a [`UICorner`](./ui-corner.md) are followed.

```luau
local gradient = Instance.new("UIGradient")
gradient.Color = ColorSequence.new(Color3.fromRGB(255, 220, 90), Color3.fromRGB(255, 120, 40))
gradient.Rotation = 90
gradient.Parent = button
```

## Properties

- `Color` - [`ColorSequence`](../datatypes/color-sequence.md), defaults to white all the way along;
- `Transparency` - [`NumberSequence`](../datatypes/number-sequence.md), defaults to `0` all the way along. Only the value of each keypoint is used, the envelope is ignored;
- `Rotation` - `number` in degrees, defaults to `0`. At `0` the gradient runs from the left edge to the right edge, at `90` from the top edge to the bottom edge. At any angle it runs from one corner or edge of the object to the opposite one;
- `Offset` - [`Vector2`](../datatypes/vector2.md), defaults to `0, 0`. Moves the gradient by that fraction of the size of the object along the direction of `Rotation`. Anything the gradient no longer reaches takes the colour of its nearest end;
- `Enabled` - `boolean`, defaults to `true`;
- `Name`, `ClassName`, `Parent`.

## Limits

- Text is not coloured by a gradient;
- Strokes and borders keep their own colour, and a `UIGradient` inside a [`UIStroke`](./ui-stroke.md) has no effect;
- On an `ImageLabel` with `ScaleType` set to `Tile` or `Slice`, a gradient with more than two keypoints is blended between the corners of each tile or slice, so it is only approximate;
- Only the first `UIGradient` inside an object is used.
