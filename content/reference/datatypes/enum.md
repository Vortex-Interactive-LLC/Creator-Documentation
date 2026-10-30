---
title: Enum
description: A data type that represents an enum
---

<!-- 
Enum
Revision 1

Written by Kindtracker on August 28th, 2026
-->

## Summary

<details>
<summary><b>Methods</b></summary>

Methods of an `Enum`.
<br><br>

* [GetEnumItems()](#getenumitems): `EnumItem[]`
* [FromName(name: `string`)](#fromnamename-string): `EnumItem | nil`
* [FromValue(value: `Number`)](#fromvaluevalue-number): `EnumItem`

</details>

## Methods

### GetEnumItems()

> `EnumItem[]`
>
> Returns an array of all `EnumItem` options available for the enum.

<br/>

### FromName(name: `string`)

> `EnumItem | nil`
>
> Finds an `EnumItem` by name.

<br/>

### FromValue(value: `Number`)

> `EnumItem`
>
> Finds an `EnumItem` by value.

<br/>

## Examples

Use an enum group to look up a named item:

```luau
local jumpKey = Enum.KeyCode:FromName("Space")

if jumpKey == Enum.KeyCode.Space then
    print("Space is the jump key")
end
```

An unknown name returns `nil`, so check user-supplied names before using the result:

```luau
local key = Enum.KeyCode:FromName("NotAKey")

if key == nil then
    print("Unknown key name")
end
```

`GetEnumItems()` is useful when building a list of allowed choices:

```luau
for _, material in ipairs(Enum.Material:GetEnumItems()) do
    print(material.Name)
end
```

`FromName("R")` returns `Enum.KeyCode.R`, and an unknown name returns `nil`.
