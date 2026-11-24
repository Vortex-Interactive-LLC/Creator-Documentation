---
title: Torque
description: Applies a constant torque to the part its attachment is on.
---

## Summary

A `Torque` spins the unanchored part that its `Attachment0` is inside. It does nothing until `Attachment0` is set, and while it is not in the `Workspace`. See the [Physics Movers guide](../../guides/physics-movers.md).

## Properties

- `Attachment0` - [`Attachment`](./attachment.md) | `nil`, the attachment whose part is spun. Defaults to `nil`;
- `Attachment1` - [`Attachment`](./attachment.md) | `nil`, used for the direction when `RelativeTo` is `Attachment1`. Defaults to `nil`;
- `RelativeTo` - `Enum.ActuatorRelativeTo`: `Attachment0` turns `Torque` with `Attachment0`, `Attachment1` turns it with `Attachment1` and does nothing while `Attachment1` is `nil`, and `World` uses `Torque` as it is. Defaults to `Attachment0`;
- `Enabled` - `boolean`, defaults to `true`. When `false` the torque is not applied;
- `Torque` - [`Vector3`](../datatypes/vector3.md), the torque applied each step. Defaults to `0, 0, 0`;
- `Name`, `ClassName`, `Parent`.
