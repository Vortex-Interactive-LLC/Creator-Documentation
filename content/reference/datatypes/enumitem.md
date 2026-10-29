---
title: EnumItem
description: An individual item in an enum
---

<!-- 
EnumItem
Revision 1

Written by Kindtracker on August 28th, 2026
-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of an `EnumItem`.
<br><br>

* [Name](#name): `string`
* [Value](#value): `Number`
* [EnumType](#enumtype): `Enum`

</details>

## Properties

### Name

> `string` 
>
> The name of the `EnumItem`.

<br/>

### Value

> `Number` 
>
> The integral value assigned to the `EnumItem`.

<br/>

### EnumType

> `Enum` 
>
> A reference to the parent `Enum` of the `EnumItem`.

<br/>

## Example

Enum items are named values. Compare the item itself in game logic, and use its properties when displaying or inspecting it:

```luau
local key = Enum.KeyCode.R

print(key.Name)     -- R
print(key.Value)    -- 114
print(key.EnumType) -- Enum.KeyCode

if key == Enum.KeyCode.R then
    print("The values match")
end
```

Avoid depending on a numeric `Value` when an enum item is available. The named item is clearer and does not require the number to remain unchanged.
