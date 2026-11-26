---
title: SurfaceAppearance
description: Replaces the color texture of a MeshPart.
---

## Summary

A `SurfaceAppearance` placed inside a [`MeshPart`](./mesh-part.md) sets the image drawn on its mesh. It takes the place of the mesh part's `TextureID`.

```luau
local appearance = Instance.new("SurfaceAppearance")
appearance.ColorMap = 123456
appearance.Parent = workspace.Statue
```

## Properties

- `ColorMap` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md) drawn on the mesh. When `0`, the mesh part's `TextureID` is used;
- `MetalnessMap`, `NormalMap`, `RoughnessMap` - `number`, image asset ids. They are accepted and saved, but not drawn yet;
- `Name`, `ClassName`, `Parent`.

## Notes

- Only a `MeshPart` uses it. Inside any other part it does nothing;
- Only the first `SurfaceAppearance` of a mesh part is used;
- The image is drawn over the part's color, so see-through areas of the image show the part's `Color`.
