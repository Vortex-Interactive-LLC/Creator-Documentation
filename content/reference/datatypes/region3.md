---
title: Region3
description: An axis-aligned box in the world.
---

## Summary

A `Region3` is a box between two corners. It is used by the [`Terrain`](../classes/terrain.md) methods.

```lua
local region = Region3.new(Vector3.new(-32, 0, -32), Vector3.new(32, 16, 32))
workspace.Terrain:FillRegion(region, 4, Enum.TerrainMaterial.Sand)
```

## Constructors

- `Region3.new(min, max)` - the corners can be given in any order.

## Properties

- `Size` - [`Vector3`](./vector3.md), the size of the box;
- `CFrame` - [`CFrame`](./cframe.md), at the centre of the box.

## Methods

- `ExpandToGrid(resolution)` - returns a `Region3` widened outward to whole multiples of `resolution`.
