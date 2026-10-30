---
title: RaycastParams
description: Parameters used to configure a raycast operation.
---

<!-- 
RaycastParams
Revision 1

Written by Kindtracker on September 19, 2026
-->

> [!NOTE]
> `RaycastParams` is currently implemented as a table and may become a datatype in the future.

## Summary

<details>
<summary><b>Properties</b></summary>

Properties of a `RaycastParams`.
<br><br>

* [FilterDescendantsInstances](#filterdescendantsinstances): `{Instance}?`
* [FilterType](#filtertype): `string`

</details>

## Properties

### FilterDescendantsInstances

> `{Instance}?`
>
> A list of instances the filter applies to. Each listed instance and all of its descendants are affected.

<br/>

### FilterType

> `string`
>
> Either `"Exclude"` or `"Include"`. With `"Exclude"`, the listed instances are ignored by the raycast. With `"Include"`, only the listed instances can be hit.

<br/>

## Example

```lua
local params = {
    FilterDescendantsInstances = { workspace.Wall },
    FilterType = "Exclude",
}

local result = workspace:Raycast(Vector3.new(0, 5, 10), Vector3.new(0, 0, -40), params)
```
