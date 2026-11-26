---
title: Beam
description: A curved ribbon drawn between two attachments.
---

## Summary

A `Beam` draws a ribbon from one [`Attachment`](./attachment.md) to another. It follows the attachments as they move.

```luau
local beam = Instance.new("Beam")
beam.Attachment0 = workspace.Start.Attachment
beam.Attachment1 = workspace.Goal.Attachment
beam.Width0 = 0.5
beam.Width1 = 0.1
beam.CurveSize0 = 6
beam.Color = ColorSequence.new(Color3.new(0.3, 0.8, 1), Color3.new(1, 0.3, 0.8))
beam.LightEmission = 1
beam.FaceCamera = true
beam.Parent = workspace
```

## Properties

- `Attachment0`, `Attachment1` - the two ends of the beam;
- `Enabled` - `boolean`, defaults to `true`;
- `Color` - [`ColorSequence`](../datatypes/color-sequence.md), color from start to end. Defaults to white;
- `Transparency` - [`NumberSequence`](../datatypes/number-sequence.md), transparency from start to end. Defaults to `0`;
- `Width0`, `Width1` - `number`, width at each end. Default to `1`;
- `CurveSize0`, `CurveSize1` - `number`, how far the curve bows out from each attachment along its `X` axis. Default to `0`;
- `Segments` - `number` from `1` to `300`, how smooth the curve is. Defaults to `10`;
- `FaceCamera` - `boolean`, turns the ribbon to face the camera. Defaults to `false`;
- `LightEmission` - `number` from `0` to `1`, `1` adds the color to what is behind it. Defaults to `0`;
- `Texture` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md). Defaults to `0`, which draws nothing;
- `TextureLength` - `number`, studs per repeat of the texture. Defaults to `1`;
- `TextureMode` - `Enum.TextureMode`, `Stretch`, `Wrap` or `Static`. Defaults to `Stretch`;
- `TextureSpeed` - `number`, how fast a `Wrap` texture scrolls. Defaults to `1`;
- `ZOffset` - `number`, pushes the beam toward the camera. Defaults to `0`;
- `Name`, `ClassName`, `Parent`.

## Notes

- The beam only draws when both attachments are inside parts in the world.
