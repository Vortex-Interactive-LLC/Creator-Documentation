---
title: Explosion
description: A blast that flings parts and breaks things apart.
---

## Summary

An `Explosion` goes off when it is parented to the world. It pushes nearby parts away, breaks their joints, kills characters, and plays a fireball.

```luau
local explosion = Instance.new("Explosion")
explosion.Position = Vector3.new(0, 10, 0)
explosion.BlastRadius = 12
explosion.BlastPressure = 800000

explosion.Hit:Connect(function(part, distance)
	print(part.Name, distance)
end)

explosion.Parent = workspace
```

## Properties

- `BlastPressure` - `number`, how hard parts are pushed. Defaults to `500000`;
- `BlastRadius` - `number` from `0` to `100`, in studs. Defaults to `4`;
- `DestroyJointRadiusPercent` - `number` from `0` to `1`, the share of the radius in which joints are broken and characters die. Defaults to `1`;
- `ExplosionType` - `Enum.ExplosionType`, defaults to `Craters`. It does not change anything yet;
- `Position` - [`Vector3`](../datatypes/vector3.md), where the blast is centered. Defaults to `0, 0, 0`;
- `TimeScale` - `number`, speed of the fireball. Defaults to `1`;
- `Visible` - `boolean`, whether the fireball is drawn. Defaults to `true`;
- `Name`, `ClassName`, `Parent`.

## Signals

- `Hit(part, distance)` - fires for every part inside the blast, with its distance from the center. It supports `Connect`, `Once`, and `Wait`.

## Notes

- Only the server runs the blast. The explosion is removed after about 3 seconds;
- Anchored parts are not pushed, but they still fire `Hit` and lose their joints inside the joint radius;
- Characters inside the joint radius die, unless they have a [`ForceField`](./force-field.md);
- Parts a player is simulating are not pushed.
