---
title: Decal
description: Draws an image on one face of a part.
---

## Summary

A `Decal` draws an image on one face of the part it is a child of. Set `Texture` to an image asset id. The image is stretched over the whole face.

```luau
local decal = Instance.new("Decal")
decal.Texture = 1234567
decal.Face = Enum.NormalId.Front
decal.Parent = workspace.Sign
```

## Properties

- `Texture` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md). Defaults to `0`, which draws nothing;
- `Face` - [`Enum.NormalId`](../datatypes/enum.md), the face of the part the image is on. Defaults to `Front`;
- `Color3` - [`Color3`](../datatypes/color3.md) that multiplies the image. Defaults to white;
- `Transparency` - `number` from `0` to `1`. Defaults to `0`;
- `ZIndex` - `number`, defaults to `1`;
- `Name`, `ClassName`, `Parent`.

## Notes

- A decal is a flat image on a face of the part's bounding box, so it fits `Block` parts best. On a ball, cylinder, or wedge it is still drawn on the box face and does not follow the shape;
- The decal is lit like the part it is on;
- A decal only draws while it is a descendant of `Workspace` and its parent is a part.
