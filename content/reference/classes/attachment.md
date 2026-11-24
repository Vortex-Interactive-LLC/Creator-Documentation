---
title: Attachment
description: A point on a part that other objects attach to.
---

## Summary

An `Attachment` marks a position and direction on the [`Part`](./part.md) it is inside. [`VectorForce`](./vector-force.md) and [`Torque`](./torque.md) use attachments to decide where and in which direction they push.

```luau
local attachment = Instance.new("Attachment")
attachment.CFrame = CFrame.new(0, 2, 0)
attachment.Parent = part
```

## Properties

- `CFrame` - [`CFrame`](../datatypes/cframe.md), the position and rotation of the attachment relative to its parent part. Defaults to the identity `CFrame`;
- `Position` - [`Vector3`](../datatypes/vector3.md), the position part of `CFrame`;
- `Orientation` - [`Vector3`](../datatypes/vector3.md), the rotation part of `CFrame`, in degrees;
- `WorldCFrame` - [`CFrame`](../datatypes/cframe.md), the position and rotation of the attachment in the world. Writing it moves the attachment to match;
- `WorldPosition` - [`Vector3`](../datatypes/vector3.md), the position of the attachment in the world;
- `WorldOrientation` - [`Vector3`](../datatypes/vector3.md), the rotation of the attachment in the world, in degrees;
- `Axis` - [`Vector3`](../datatypes/vector3.md), the direction the attachment's X axis points in, relative to its parent part;
- `SecondaryAxis` - [`Vector3`](../datatypes/vector3.md), the direction the attachment's Y axis points in, relative to its parent part;
- `WorldAxis` - [`Vector3`](../datatypes/vector3.md), the same as `Axis`, in the world;
- `WorldSecondaryAxis` - [`Vector3`](../datatypes/vector3.md), the same as `SecondaryAxis`, in the world;
- `Visible` - `boolean`, defaults to `false`. Whether a marker is drawn at the attachment;
- `Name`, `ClassName`, `Parent`.
