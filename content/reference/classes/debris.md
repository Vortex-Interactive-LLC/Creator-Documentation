---
title: Debris
description: A service that allows removal of instances without yielding
---

<!--
Debris
Revision 1

Written by TheJustDare on August 30th, 2026
-->

## Summary

<details>
<summary><b>Methods</b></summary>
Methods available on `Debris`.
<br><br>

* [AddItem](#additem)
* [SetMaxItems](#setmaxitems)

</details>

## Overview

`Debris` is a service that allows instances that may lose utility after a set period of time to be removed without yielding
```lua
local Debris = game:GetService("Debris")

local part = Instance.new("Part")
part.Parent = workspace

Debris:AddItem(part, 5)
```

## Methods

### AddItem

> `Debris:AddItem(instance: Instance, lifetime: Number)`
>
> Schedules `instance` for removal after `lifetime` seconds without yielding.

#### Parameters

- `instance`: `Instance` — the instance to remove.
- `lifetime`: `Number` — the delay before removal, in seconds.

<br/>

### SetMaxItems

> `Debris:SetMaxItems(maxItems: Number)`
>
> Sets the service's maximum number of tracked items.

#### Parameters

- `maxItems`: `Number` — the maximum number of tracked items.

## Testing Notes

The exposed methods were revalidated in Vortex Studio 0.3.4; detailed
method behavior may differ in later releases.

`AddItem` and `SetMaxItems` are exposed in both `Script` and `LocalScript`.
Calling `Debris:AddItem(part, 0)` removed an unparented temporary `Part` within
two scheduler ticks. The held Lua reference then reported `ClassName` as
`Instance` and an empty `Name`.
