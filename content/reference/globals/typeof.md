---
title: typeof
description: Returns the type of a value as a string.
---

`typeof(value)` returns the type of `value` as a string.

```lua
print(typeof(5))                -- number
print(typeof(Vector3.new()))    -- Vector3
print(typeof(workspace))        -- Instance
print(typeof(Enum.Material.Plastic)) -- EnumItem
```

| Value | Result |
| --- | --- |
| numbers, strings, booleans, `nil`, functions, tables, threads | `number`, `string`, `boolean`, `nil`, `function`, `table`, `thread` |
| `Vector2`, `Vector3`, `CFrame`, `Color3`, `UDim`, `UDim2` | the datatype name |
| any Instance, including `workspace`, `game`, and services such as `Players` and `ReplicatedStorage` | `Instance` |
| `RunService`, `TweenService`, and `Debris` | `table` |
| an enum item, such as `Enum.Material.Plastic` | `EnumItem` |
| an enum, such as `Enum.Material` | `Enum` |
| `TweenInfo` | `table` |

Use `typeof` instead of `type` when you need to tell Vortex datatypes and Instances apart. `type` returns `"table"` for all of them.
