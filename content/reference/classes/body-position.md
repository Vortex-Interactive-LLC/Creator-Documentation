---
title: BodyPosition
description: Pulls an unanchored part toward a world position.
---

## Summary

Place a `BodyPosition` inside a `Part` to affect it. See the [Physics Movers guide](../../guides/physics-movers.md).

## Properties

- `Position` - [`Vector3`](../datatypes/vector3.md), the world position to move toward. Defaults to `0, 0, 0`;
- `MaxForce` - [`Vector3`](../datatypes/vector3.md), the most force applied on each axis. Defaults to `4000, 4000, 4000`;
- `P` - `number`, the strength of the pull. Defaults to `10000`;
- `D` - `number`, how strongly it resists the part's motion. Defaults to `1250`;
- `Name`, `ClassName`, `Parent`.
