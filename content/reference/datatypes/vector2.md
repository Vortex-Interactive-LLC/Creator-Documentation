---
title: Vector2
description: A two-dimensional vector.
---

## Summary

A pair of numbers, used for screen positions and sizes such as the mouse location and the camera's viewport size.

```lua
local v = Vector2.new(3, 4)
print(v.Magnitude) --> 5
print(v.Unit)      --> 0.6, 0.8
```

## Constructors

- `Vector2.new(x: number, y: number)` - creates a vector. With no arguments it is `0, 0`.

## Constants

- `Vector2.zero` - `0, 0`;
- `Vector2.one` - `1, 1`;
- `Vector2.xAxis` - `1, 0`;
- `Vector2.yAxis` - `0, 1`.

## Properties

- `X`, `Y` - the components. Lowercase `x` and `y` also work;
- `Magnitude` - the length of the vector;
- `Unit` - the vector with a length of 1. The unit of a zero vector is `Vector2.zero`.

## Methods

- `Dot(other: Vector2): number` - the dot product;
- `Lerp(other: Vector2, alpha: number): Vector2` - interpolates between the two vectors.

## Operators

`+` and `-` between two vectors, `*` and `/` by a number or component by component with another vector, unary `-`, and `==`. Adding a plain number to a vector raises an error.

A `Vector2` can be sent through a `RemoteEvent`. See [Remote Events](../../guides/remote-events.md).
