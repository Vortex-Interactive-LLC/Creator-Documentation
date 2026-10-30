---

title: Color3
description: A color value comprised of red, green, and blue components.
---

<!-- 
Color3
Revision 1

Written by Kindtracker on August 28th, 2026
-->

> [!NOTE]
> There will be more things (methods, constructors, properties, etc.) in the future.

## Summary

<details>
<summary><b>Properties</b></summary>

Properties of a `Color3`.
<br><br>

* [R](#r): `Number`
* [G](#g): `Number`
* [B](#b): `Number`

</details>

<details>
<summary><b>Constructors</b></summary>

Constructors of a `Color3`.
<br><br>

* [new(R: `Number`, G: `Number`, B: `Number`)](#newr-number-g-number-b-number): `Color3`
* [fromRGB(R: `Number`, G: `Number`, B: `Number`)](#fromrgbr-number-g-number-b-number): `Color3`

</details>

<details>
<summary><b>Methods</b></summary>

Methods of a `Color3`.
<br><br>

* [Lerp](#lerp): `Color3`

</details>

## Properties

### R

> `Number`
>
> The red value of the color.

<br/>

### G

> `Number`
>
> The green value of the color.

<br/>

### B

> `Number`
>
> The blue value of the color.

<br/>

## Constructors

### new(R: `Number`, G: `Number`, B: `Number`)

> `Color3`
>
> Returns a new `Color3` from the given values. Values range from `0` to `1`.

<br/>

### fromRGB(R: `Number`, G: `Number`, B: `Number`)

> `Color3`
>
> Returns a new `Color3` from the given values. Values range from `0` to `255`.

<br/>

## Methods

### Lerp()

> `Color3`
>
> `color:Lerp(other: Color3, alpha: Number)`
>
> Returns a component-wise linear interpolation between `color` and `other`.

#### Parameters

- `other`: `Color3` — the target color.
- `alpha`: `Number` — the interpolation amount, from `0` to `1`.

<br/>

## Examples

Use `fromRGB` when working with familiar `0` to `255` color values. Use `new` when the components are already normalized from `0` to `1`:

```luau
local orangeFromRGB = Color3.fromRGB(255, 128, 0)
local orangeNormalized = Color3.new(1, 128 / 255, 0)

local part = workspace:FindFirstChild("MyPart")
if part then
    part.Color = orangeFromRGB
end
```

`Lerp` creates a color between two endpoints. An `alpha` of `0` returns the starting color, `1` returns the target, and `0.5` returns the midpoint:

```luau
local red = Color3.fromRGB(255, 0, 0)
local blue = Color3.fromRGB(0, 0, 255)
local purple = red:Lerp(blue, 0.5)
```

## Testing Notes

The previously listed `Color3.fromHSV` and `Color3.fromHex` constructors were removed from this reference because they are not exposed.

In the examples above, `Color3.fromRGB(255, 128, 0)` produces approximately `(1, 0.502, 0)`, and the red-to-blue midpoint produces `(0.5, 0, 0.5)`.
