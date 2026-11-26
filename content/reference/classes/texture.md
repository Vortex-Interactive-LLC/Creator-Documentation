---
title: Texture
description: Tiles an image over one face of a part.
---

## Summary

A `Texture` repeats an image over one face of the part it is a child of. It works like a [`Decal`](./decal.md), but the image is tiled instead of stretched. For your own images, see [Meshes & Textures](../../guides/meshes-and-textures.md).

```luau
local texture = Instance.new("Texture")
texture.Texture = 1234567
texture.Face = Enum.NormalId.Top
texture.StudsPerTileU = 4
texture.StudsPerTileV = 4
texture.Parent = workspace.Floor
```

## Properties

- `Texture` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md). Defaults to `0`, which draws nothing;
- `Face` - [`Enum.NormalId`](../datatypes/enum.md), the face of the part the image is on. Defaults to `Front`;
- `StudsPerTileU`, `StudsPerTileV` - `number`, how many studs one copy of the image covers across and up the face. Defaults to `2`;
- `OffsetStudsU`, `OffsetStudsV` - `number`, shifts the tiling across the face. Defaults to `0`;
- `Color3` - [`Color3`](../datatypes/color3.md) that multiplies the image. Defaults to white;
- `Transparency` - `number` from `0` to `1`. Defaults to `0`;
- `ZIndex` - `number`, defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

The notes on [`Decal`](./decal.md) apply: flat faces only, lit like the part, and drawn only inside `Workspace`.
