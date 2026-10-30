---
title: Physics Movers
description: Push, steer, and hold unanchored parts with BodyVelocity, BodyPosition, forces, and torques.
---
Physics movers are objects you place inside an unanchored `Part` to make physics push it. They are applied continuously while they are parented to the part.

```luau
local part = Instance.new("Part")
part.Anchored = false
part.Parent = workspace

local mover = Instance.new("BodyVelocity")
mover.Velocity = Vector3.new(10, 0, 0)
mover.MaxForce = Vector3.new(1e6, 1e6, 1e6)
mover.Parent = part
```

Movers act on the unanchored part they are inside. The velocity and position movers have no effect on an anchored part, while `VectorForce` and `Torque` apply a force and torque to whatever body they are parented to.

## The movers

| Class | What it does | Properties (default) |
| --- | --- | --- |
| [`BodyVelocity`](../reference/classes/body-velocity.md) | Pushes the part toward a target velocity. | `Velocity` (`0, 2, 0`), `MaxForce` (`4000, 4000, 4000`), `P` (`1250`) |
| [`BodyPosition`](../reference/classes/body-position.md) | Pulls the part toward a world position and damps its motion. | `Position` (`0, 0, 0`), `MaxForce` (`4000, 4000, 4000`), `P` (`10000`), `D` (`1250`) |
| [`BodyAngularVelocity`](../reference/classes/body-angular-velocity.md) | Spins the part toward a target angular velocity. | `AngularVelocity` (`0, 2, 0`), `MaxTorque` (`4000, 4000, 4000`), `P` (`1250`) |
| [`VectorForce`](../reference/classes/vector-force.md) | Applies a constant force. | `Force` (`0, 0, 0`) |
| [`Torque`](../reference/classes/torque.md) | Applies a constant torque. | `Torque` (`0, 0, 0`) |

`P` controls how strongly the mover corrects toward its target, and `D` how strongly `BodyPosition` resists motion. `MaxForce` and `MaxTorque` limit the effort per axis. 

Several movers on one part add together. Removing a mover, or setting its parent to `nil`, stops its effect.

## Holding a part in the air

```luau
local hold = Instance.new("BodyPosition")
hold.Position = Vector3.new(0, 30, 0)
hold.MaxForce = Vector3.new(1e6, 1e6, 1e6)
hold.Parent = part
```

> [!NOTE]
> Moving a part with movers is different from moving it by setting `Position` or by tweening it. Movers go through the physics simulation, so the part collides with other parts along the way. See [Tweening](tweening.md) for scripted motion.
