---
title: Beams & Trails
description: Draw a ribbon between two points, or behind a moving part.
---
`Beam` and `Trail` both draw a ribbon between two [`Attachment`](../reference/classes/attachment.md) objects. A beam stretches between them. A trail follows them as they move.

## Attachments

An `Attachment` is a point on a part. Add two, and set `Position` to place each one.

```luau
local function attach(part, offset)
	local attachment = Instance.new("Attachment")
	attachment.Position = offset
	attachment.Parent = part
	return attachment
end
```

## Beam

A [`Beam`](../reference/classes/beam.md) connects `Attachment0` and `Attachment1` and follows them if the parts move.

```luau
local beam = Instance.new("Beam")
beam.Attachment0 = attach(workspace.Start, Vector3.new(0, 1, 0))
beam.Attachment1 = attach(workspace.End, Vector3.new(0, 1, 0))
beam.Width0 = 0.5
beam.Width1 = 0.1
beam.Color = ColorSequence.new(Color3.new(0.3, 0.7, 1))
beam.LightEmission = 1
beam.Parent = workspace.Start
```

- `Width0` and `Width1` set the width at each end;
- `CurveSize0` and `CurveSize1` bend the beam along each attachment's X axis. `Segments` sets how smooth the curve is;
- `FaceCamera` keeps the beam turned toward the player. When off, the beam is flat;
- `Texture` repeats an image along the beam. `TextureLength` sets how long one copy is, `TextureMode` chooses `Stretch`, `Wrap`, or `Static`, and `TextureSpeed` scrolls it.

## Trail

A [`Trail`](../reference/classes/trail.md) leaves a ribbon behind the attachments while they move. The ribbon fades over `Lifetime`.

```luau
local trail = Instance.new("Trail")
trail.Attachment0 = attach(sword, Vector3.new(0, 0, -2))
trail.Attachment1 = attach(sword, Vector3.new(0, 0, 2))
trail.Lifetime = 0.4
trail.Transparency = NumberSequence.new(0.2, 1)
trail.Parent = sword
```

- `WidthScale` and `Transparency` change along the length of the trail, from newest to oldest;
- `MinLength` is how far the attachments move before a new piece is added. `MaxLength` limits the total length, and `0` means no limit;
- `Clear()` removes the trail, for example after a teleport.

## Notes

- Both are drawn on the client. A player who joins late sees a short trail that grows as the parts move;
- A beam or trail without both attachments draws nothing;
- Set `Enabled` to `false` to hide one.
