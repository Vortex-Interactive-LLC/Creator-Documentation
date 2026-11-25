---
title: Terrain
description: The voxel terrain of a game and the look of its water.
---

## Summary

`Terrain` holds the voxel terrain of a game and the settings that control how its water looks. It is `workspace.Terrain`, and it shows in the Studio Explorer next to `Lighting`. See the [Water guide](../../guides/water.md).

`Terrain` cannot be created or destroyed. Terrain is made of cells that are 4 studs wide. Each cell has a [`Enum.TerrainMaterial`](./enum.md) and an occupancy from `0` (empty) to `1` (full). Solid cells are drawn as a smooth surface that players can walk on. Water cells fill with water, and players can swim in them.

Methods that change terrain only work in server scripts. Methods that read it work anywhere.

```lua
local terrain = workspace.Terrain
terrain:FillBall(Vector3.new(0, 10, 0), 20, Enum.TerrainMaterial.Rock)
terrain:FillBlock(CFrame.new(60, 0, 0), Vector3.new(40, 8, 40), Enum.TerrainMaterial.Water)
```

## Properties

- `WaterColor` - [`Color3`](../datatypes/color3.md), the colour of the water. Defaults to `12, 84, 92`;
- `WaterReflectance` - `number` from `0` to `1`, how strongly the water reflects the sky and the sun. Defaults to `1`;
- `WaterTransparency` - `number` from `0` to `1`. `0` is opaque and `1` is clear. Defaults to `0.3`;
- `WaterWaveSize` - `number` from `0` to `2`, how tall the waves are. `0` is a flat surface. Defaults to `0.4`;
- `WaterWaveSpeed` - `number` from `0` to `10`, how fast the waves move. Defaults to `1`;
- `MaterialColors` - `string`, the colours set with `SetMaterialColor`. Use the methods instead of editing it.

Values outside the range are clamped.

## Methods

Filling:

- `FillBlock(cframe, size, material)` - fills a box;
- `FillBall(center, radius, material)` - fills a sphere;
- `FillCylinder(cframe, height, radius, material)` - fills a cylinder standing along the `Y` axis of `cframe`;
- `FillWedge(cframe, size, material)` - fills a wedge;
- `FillRegion(region, resolution, material)` - fills a [`Region3`](../datatypes/region3.md). `resolution` must be `4`;
- `Clear()` - removes all terrain.

Filling with `Enum.TerrainMaterial.Air` carves terrain away. Filling with `Enum.TerrainMaterial.Water` only fills empty cells, and never removes solid terrain.

Reading and writing cells. `resolution` must be `4`, and the region is widened to whole cells:

- `ReadVoxels(region, resolution)` - returns two 3D arrays indexed `[x][y][z]`: the materials and the occupancies from `0` to `1`;
- `WriteVoxels(region, resolution, materials, occupancy)` - writes arrays of the same shape that `ReadVoxels` returns. They must match the size of the region;
- `ReplaceMaterial(region, resolution, from, to)` - changes every `from` cell in the region into `to`;
- `CopyRegion(region)` - returns a [`TerrainRegion`](../datatypes/terrain-region.md) with a copy of the cells;
- `PasteRegion(terrainRegion, corner, pasteEmptyCells)` - writes a `TerrainRegion` back with its lowest corner at the cell `corner`, a [`Vector3int16`](../datatypes/vector3int16.md). Empty cells are skipped unless `pasteEmptyCells` is `true`.

Colours:

- `SetMaterialColor(material, color)` - changes the colour of a material for everyone;
- `GetMaterialColor(material)` - returns the colour of a material.

Converting:

- `WorldToCell(position)` - returns the cell that holds a world position, as a `Vector3`;
- `CellCenterToWorld(x, y, z)` - returns the world position of the middle of a cell.

A region that holds more than about four million cells errors. A game can hold up to 16,384 terrain chunks (each 64 studs wide) before writes error.

## Notes

The water settings apply to every water region and every body of terrain water. A region has no look of its own.
