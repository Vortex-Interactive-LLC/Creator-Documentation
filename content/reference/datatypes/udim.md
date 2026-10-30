---
title: UDim
description: A one-dimensional size made of a scale and a pixel offset.
---

## Summary

A `UDim` describes one dimension of a GUI size or position as a fraction of the parent (`Scale`) plus a number of pixels (`Offset`). Two of them make a [`UDim2`](./udim2.md).

```lua
local half = UDim.new(0.5, 10) -- half the parent, plus 10 pixels
print(half.Scale, half.Offset) --> 0.5 10
```

## Constructors

- `UDim.new(scale: number, offset: number)`.

## Properties

- `Scale` - `number`;
- `Offset` - `number`.

## Operators

`+`, `-`, and `==` between two `UDim`s.
