---
title: BodyVelocity
description: Pushes an unanchored part toward a target velocity.
---

## Summary

Place a `BodyVelocity` inside a `Part` to affect it. See the [Physics Movers guide](../../guides/physics-movers.md).

## Properties

- `Velocity` - [`Vector3`](../datatypes/vector3.md), the target velocity. Defaults to `0, 2, 0`;
- `MaxForce` - [`Vector3`](../datatypes/vector3.md), the most force applied on each axis. Defaults to `4000, 4000, 4000`;
- `P` - `number`, how strongly it corrects toward the target. Defaults to `1250`;
- `Name`, `ClassName`, `Parent`.
