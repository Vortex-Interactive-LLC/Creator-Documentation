---
title: Debris
description: Access the Debris cleanup service.
---

> [!Summary]
> Debris is the cleanup service used to remove objects after a delay. Use `game:GetService("Debris")` to schedule cleanup, and keep in mind that current Vortex support is limited to basic item removal flows.

`Debris` is available through `game:GetService("Debris")` in both Script and LocalScript. See the [Debris service reference](../classes/debris.md) for its methods and current runtime limits.

`Debris:AddItem(instance, 0)` removed an unparented temporary Part within two scheduler ticks in Vortex Studio 0.3.4. `AddItem` and `SetMaxItems` are both exposed.
