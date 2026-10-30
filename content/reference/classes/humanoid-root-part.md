---
title: HumanoidRootPart
description: The root Part of a visible Player Character.
---

`HumanoidRootPart` is the root object exposed by a visible player's Character model. It reports `ClassName == "Part"`, but it is a narrow character-state projection rather than a normal [`Part`](./part.md) instance. It is not a separately constructible Vortex class; access it from the character that Vortex exposes:

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

These fields are readable in both a `LocalScript` and a server `Script`:

- `ClassName`, with the value `"Part"`;
- `Name`, with the value `"HumanoidRootPart"`;
- `Parent`, the visible Character Model;
- `Position`, a [`Vector3`](../datatypes/vector3.md);
- `Size`, a [`Vector3`](../datatypes/vector3.md);
- `CFrame`, a [`CFrame`](../datatypes/cframe.md).

`IsA` is the only method exposed. It returns `true` for `"Part"` and `"BasePart"`.

Ordinary Part fields such as `Anchored` and `CanCollide` read as `nil`, and the Instance methods other than `IsA` (hierarchy, `Clone`, `Destroy`, attributes, and property signals) are not available.

## Writing

`HumanoidRootPart.Size` is read-only: assigning it raises an error saying that character state is server-authoritative. Assigning `Position`, `CFrame`, `Orientation`, or `Rotation` from a server `Script` is accepted and moves or turns the character. You can also use `Character:MoveTo()` or `Character:PivotTo()`.

This applies to the live character root part only; ordinary script-created Parts have writable transform properties.
