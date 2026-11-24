---
title: VectorForce
description: Applies a constant force to the part its attachment is on.
---

## Summary

A `VectorForce` pushes the unanchored part that its `Attachment0` is inside. It does nothing until `Attachment0` is set, and while it is not in the `Workspace`. See the [Physics Movers guide](../../guides/physics-movers.md).

```luau
local attachment = Instance.new("Attachment")
attachment.Parent = part

local force = Instance.new("VectorForce")
force.Attachment0 = attachment
force.Force = Vector3.new(0, 5000, 0)
force.RelativeTo = Enum.ActuatorRelativeTo.World
force.Parent = part
```

## Properties

- `Attachment0` - [`Attachment`](./attachment.md) | `nil`, the attachment the force is applied at. The part it is inside is the part that moves. Defaults to `nil`;
- `Attachment1` - [`Attachment`](./attachment.md) | `nil`, used for the direction when `RelativeTo` is `Attachment1`. Defaults to `nil`;
- `Force` - [`Vector3`](../datatypes/vector3.md), the force applied each step. Defaults to `1000, 0, 0`;
- `RelativeTo` - `Enum.ActuatorRelativeTo`: `Attachment0` turns `Force` with `Attachment0`, `Attachment1` turns it with `Attachment1` and does nothing while `Attachment1` is `nil`, and `World` uses `Force` as it is. Defaults to `Attachment0`;
- `ApplyAtCenterOfMass` - `boolean`, defaults to `false`. When `true`, the force is applied at the center of mass and does not spin the part. When `false`, it is applied at `Attachment0` and can spin the part;
- `Enabled` - `boolean`, defaults to `true`. When `false` the force is not applied;
- `Name`, `ClassName`, `Parent`.
