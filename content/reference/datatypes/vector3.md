---
title: Vector3
description: A three-dimensional vector
---

<!-- 
Vector3
Revision 1

Written by Kindtracker on August 28th, 2026

Revision 2

Written by CNK (Vortex IG. CNK) on Aug 30th, 2026 based on actual code.
-->

## Summary

<details>
<summary><b>Properties</b></summary>

Properties of a `Vector3`.
<br><br>

* [zero](#zero): `Vector3`
* [one](#one): `Vector3`
* [xAxis](#xaxis): `Vector3`
* [yAxis](#yaxis): `Vector3`
* [zAxis](#zaxis): `Vector3`
* [X](#x): `Number`
* [Y](#y): `Number`
* [Z](#z): `Number`
* [Magnitude](#magnitude): `Number`
* [Unit](#unit): `Vector3`

</details>

<details>
<summary><b>Constants</b></summary>

Constants of a `Vector3`.
<br><br>

* [zero](#zero): `Vector3`
* [one](#one): `Vector3`
* [xAxis](#xaxis): `Vector3`
* [yAxis](#yaxis): `Vector3`
* [zAxis](#zaxis): `Vector3`

</details>

<details>
<summary><b>Constructors</b></summary>

Constructors of a `Vector3`.
<br><br>

* [new(X: `Number`, Y: `Number`, Z: `Number`)](#newx-number-y-number-z-number): `Vector3`

</details>

<details>
<summary><b>Methods</b></summary>

Methods of a `Vector3`.
<br><br>

* [Cross](#crossother-vector3): `Vector3`
* [Dot](#dotother-vector3): `Number`
* [Lerp](#lerpother-vector3-alpha-number): `Vector3`
* [tostring(Vector3)](#tostringvector3): `string`

</details>

## Properties

### X

> `Number` 
>
> The X-axis component of the vector.

<br/>

### Y

> `Number` 
>
> The Y-axis component of the vector.

<br/>

### Z

> `Number` 
>
> The Z-axis component of the vector.

<br/>

### Magnitude

> `Number`
>
> The magnitude (aka. length) of the vector.

<br/>

### Unit

> `Vector3`
>
> The normalized vector.

<br/>

## Constants

### zero

> `Vector3`
>
> `Vector3.zero`
>
> The vector `(0, 0, 0)`.

<br/>

### one

> `Vector3`
>
> `Vector3.one`
>
> The vector `(1, 1, 1)`.

<br/>

### xAxis

> `Vector3`
>
> `Vector3.xAxis`
>
> The unit vector along the X axis, `(1, 0, 0)`.

<br/>

### yAxis

> `Vector3`
>
> `Vector3.yAxis`
>
> The unit vector along the Y axis, `(0, 1, 0)`.

<br/>

### zAxis

> `Vector3`
>
> `Vector3.zAxis`
>
> The unit vector along the Z axis, `(0, 0, 1)`.

<br/>

## Constructors

### new(X: `Number`, Y: `Number`, Z: `Number`)

> `Vector3` 
>
> Returns a new `Vector3` from the given components.

<br/>

## Methods

### Dot(other: `Vector3`)

> `Vector3`
>
> Returns the dot product of two vectors. 

<br/>

### Cross(other: `Vector3`)

> `Vector3`
>
> Returns the cross product of two vectors. 

### Lerp(other: `Vector3`, alpha: `Number`)

> `Vector3`
>
> Returns an interpolated vector between `self` and `other`. 
> 
> When alpha is `0.0` it returns `self`; when `alpha` is `0.5` it returns the vector directly between `self` and `other`; when `alpha` is `1.0` it returns `other`.

## Operators

### `Vector3` + `Vector3`

> `Vector3`
>
> Adds the components of two vectors.

<br/>

### `Vector3` - `Vector3`

> `Vector3`
>
> Subtracts the components of two vectors.

<br/>

### `Vector3` * `Vector3 | Number`

> `Vector3`
>
> Multiplies component-wise if both operands are `Vector3`, or scales every component if one operand is a `Number`.

<br/>

### `Vector3` / `Vector3 | Number`

> `Vector3`
>
> Divides component-wise if both operands are `Vector3`, or scales every component if the denominator is a `Number`.

<br/>

### -Vector3

> `Vector3`
>
> Returns the negation of the vector.

<br/>

### Vector3 == Vector3

> `Boolean`
>
> Returns whether two vectors have equal `X`, `Y`, and `Z` components.

<br/>

### tostring(Vector3)

> `string`
>
> Formats the vector as `"X, Y, Z"` with 3 decimal places, e.g. `"1.000, 2.000, 3.000"`.

<br/>
