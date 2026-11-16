---
title: Terrain
description: The settings that control how every body of water in a game looks.
---

## Summary

`Terrain` holds the look of all the water in a game. It appears in the Studio Explorer next to `Lighting`, and its properties are set in Studio's Properties panel. See the [Water guide](../../guides/water.md).

`Terrain` cannot be created or destroyed. Scripts cannot reach it yet, so these settings can only be changed in Studio.

## Properties

- `WaterColor` - [`Color3`](../datatypes/color3.md), the colour of the water. Defaults to `12, 84, 92`;
- `WaterReflectance` - `number` from `0` to `1`, how strongly the water reflects the sky and the sun. Defaults to `1`;
- `WaterTransparency` - `number` from `0` to `1`. `0` is opaque and `1` is clear. Defaults to `0.3`;
- `WaterWaveSize` - `number` from `0` to `2`, how tall the waves are. `0` is a flat surface. Defaults to `0.4`;
- `WaterWaveSpeed` - `number` from `0` to `10`, how fast the waves move. Defaults to `1`.

Values outside the range are clamped.

## Notes

The settings apply to every water region in the game. A region has no look of its own.

The water look is saved in the game file along with the rest of the place, and changes can be undone and are shared in a team session.
