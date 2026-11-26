---
title: ParticleEmitter
description: Emits particles from a part or attachment.
---

## Summary

A `ParticleEmitter` spawns small camera-facing sprites from the part or [`Attachment`](./attachment.md) it is parented to.

```luau
local emitter = Instance.new("ParticleEmitter")
emitter.Rate = 40
emitter.Lifetime = NumberRange.new(1, 2)
emitter.Speed = NumberRange.new(6, 10)
emitter.SpreadAngle = Vector2.new(20, 20)
emitter.Size = NumberSequence.new(1, 0)
emitter.Color = ColorSequence.new(Color3.new(1, 0.6, 0.1), Color3.new(1, 0, 0))
emitter.Parent = workspace.Part
```

## Properties

- `Enabled` - `boolean`, defaults to `true`;
- `Rate` - `number` from `0` to `10000`, particles per second. Defaults to `20`;
- `Lifetime` - [`NumberRange`](../datatypes/number-range.md), seconds a particle lives, up to `600`. Defaults to `5, 10`;
- `Speed` - [`NumberRange`](../datatypes/number-range.md), initial speed in studs per second. Defaults to `5, 5`;
- `SpreadAngle` - [`Vector2`](../datatypes/vector2.md), cone angle in degrees on each axis, from `0` to `180`. Defaults to `0, 0`;
- `Acceleration` - [`Vector3`](../datatypes/vector3.md), constant acceleration. Defaults to `0, 0, 0`;
- `Drag` - `number` from `0` to `1000`, how fast particles slow down. Defaults to `0`;
- `Rotation` - [`NumberRange`](../datatypes/number-range.md), starting rotation in degrees. Defaults to `0, 0`;
- `RotSpeed` - [`NumberRange`](../datatypes/number-range.md), rotation speed in degrees per second. Defaults to `0, 0`;
- `Size` - [`NumberSequence`](../datatypes/number-sequence.md), size over the particle's life. Defaults to `1`;
- `Transparency` - [`NumberSequence`](../datatypes/number-sequence.md), transparency over life. Defaults to `0`;
- `Color` - [`ColorSequence`](../datatypes/color-sequence.md), color over life. Defaults to white;
- `Texture` - `number`, the asset id of an [uploaded image](../../guides/meshes-and-textures.md). Defaults to `0`, which draws nothing;
- `LightEmission` - `number` from `0` to `1`, how additive the blend is. Defaults to `0`;
- `LightInfluence` - `number` from `0` to `1`. Defaults to `1`. It is saved but does not change the picture yet;
- `Brightness` - `number` from `0` to `1000`, brightness multiplier. Defaults to `1`;
- `Orientation` - `Enum.ParticleOrientation`, defaults to `FacingCamera`;
- `ZOffset` - `number`, pushes particles toward or away from the camera. Defaults to `0`;
- `LockedToPart` - `boolean`, particles move with the part. Defaults to `false`;
- `EmissionDirection` - `Enum.NormalId`, the face particles leave from. Defaults to `Top`;
- `Shape` - `Enum.ParticleEmitterShape`, defaults to `Box`;
- `ShapeStyle` - `Enum.ParticleEmitterShapeStyle`, defaults to `Volume`;
- `ShapeInOut` - `Enum.ParticleEmitterShapeInOut`, defaults to `Outward`;
- `ShapePartial` - `number` from `0` to `1`, defaults to `1`. It is saved but does not change the picture yet;
- `VelocityInheritance` - `number` from `0` to `1`, how much of the part's velocity particles inherit. Defaults to `0`;
- `TimeScale` - `number` from `0` to `100`, speed of the simulation. Defaults to `1`;
- `FlipbookLayout` - `Enum.ParticleFlipbookLayout`, defaults to `None`;
- `FlipbookMode` - `Enum.ParticleFlipbookMode`, defaults to `Loop`;
- `FlipbookFramerate` - [`NumberRange`](../datatypes/number-range.md), frames per second, up to `120`. Defaults to `1, 1`;
- `FlipbookStartRandom` - `boolean`, defaults to `false`;
- `Name`, `ClassName`, `Parent`.

## Methods

- `Emit(count)` - emits `count` particles at once. `count` defaults to `1` and is capped at `1000`;
- `Clear()` - removes every live particle.

## Notes

- The emitter must be parented to a part or an `Attachment` to show;
- Emitters are drawn on the client and do not collide.
