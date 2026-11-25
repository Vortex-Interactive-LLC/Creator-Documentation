---
title: TerrainRegion
description: A copy of a block of terrain cells.
---

## Summary

A `TerrainRegion` is returned by [`Terrain:CopyRegion`](../classes/terrain.md). It holds a copy of the cells, and it can be written back with `Terrain:PasteRegion`. There is no constructor, and it has no properties.

```lua
local copy = workspace.Terrain:CopyRegion(Region3.new(Vector3.new(0, 0, 0), Vector3.new(32, 32, 32)))
workspace.Terrain:PasteRegion(copy, Vector3int16.new(20, 0, 0), false)
```
