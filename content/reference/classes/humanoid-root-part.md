---
title: HumanoidRootPart
description: The root Part of a visible Player Character.
---

`HumanoidRootPart` is the root object exposed by a visible player's Character
model. It reports `ClassName == "Part"`, but it is a narrow character-state
projection rather than a normal [`Part`](./part.md) instance. It is not a
separately constructible Vortex class; access it from the character that
Vortex exposes:

```luau
-- LocalScript
local rootPart = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
```

A server `Script` can read the same projection from the first visible player:

```luau
local player = game:GetService("Players"):GetPlayers()[1]
local rootPart = player.Character.HumanoidRootPart
```

## Confirmed surface

In Vortex Studio 0.3.4, these fields are readable in both a `LocalScript` and
a confirmed server `Script`:

- `ClassName`, with the value `"Part"`;
- `Name`, with the value `"HumanoidRootPart"`;
- `Parent`, the visible Character Model;
- `Position`, a [`Vector3`](../datatypes/vector3.md);
- `Size`, a [`Vector3`](../datatypes/vector3.md).

`IsA` is the only tested method currently exposed. It returns `true` for
`"Part"`, `"BasePart"`, and `"Instance"`, despite the narrow projection
surface described below.

The tested ordinary Part fields are unavailable: `Anchored`, `CanCollide`,
`CastShadow`, `CFrame`, `Color`, `Material`, `Orientation`, `Rotation`,
`Transparency`, and the tested velocity, mass, collision-query, touch, and
root-priority fields all read as `nil`.

The tested Instance, Part, and physics members—including hierarchy, cloning,
destruction, attributes, property signals, joints, impulses, mass, and network
ownership methods—also read as `nil`. `Changed`, `Touched`, `TouchEnded`, and
the tested hierarchy/lifecycle signals read as `nil`; none is connectable.

## Character-state authority

Writing `HumanoidRootPart.Position`, `HumanoidRootPart.Size`, or
`HumanoidRootPart.Orientation` is rejected in both a `LocalScript` and a
confirmed server `Script`. The current error describes the property as read-only in 
a LocalScript and says character state is server-authoritative, even when
`RunService:IsServer()` reports `true`.

Consequently, do not use the visible character root part as a target for 
server-side teleportation, resizing, or movement control target in the current runtime. This is a
restriction of the live Character projection; it does not describe ordinary
script-created Parts, whose tested transform properties remain writable.

## Testing Notes

These observations were verified in Vortex Studio 0.3.4; untested members may
exist in later runtime releases.
