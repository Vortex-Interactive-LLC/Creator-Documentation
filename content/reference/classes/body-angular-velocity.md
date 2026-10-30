---
title: BodyAngularVelocity
description: Spins an unanchored part toward a target angular velocity.
---

## Summary

Place a `BodyAngularVelocity` inside a `Part` to affect it. See the [Physics Movers guide](../../guides/physics-movers.md).

## Properties

- `AngularVelocity` - [`Vector3`](../datatypes/vector3.md), the target angular velocity. Defaults to `0, 2, 0`;
- `MaxTorque` - [`Vector3`](../datatypes/vector3.md), the most torque applied on each axis. Defaults to `4000, 4000, 4000`;
- `P` - `number`, how strongly it corrects toward the target. Defaults to `1250`;
- `Name`, `ClassName`, `Parent`.
