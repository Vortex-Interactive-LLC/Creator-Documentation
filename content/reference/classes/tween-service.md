---
title: TweenService
description: Creates Tween objects for instance-property animation.
---

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of `TweenService`.
<br><br>

* [Create](#create): `Tween`

</details>

## Overview

Service that is used to create a tween. A tween is a smooth interpolation between two states over a period of time. 

`TweenService` is available through `game:GetService("TweenService")` or like a global `TweenService`.

## Methods

### Create

> `Create(instance: Instance, tweenInfo: TweenInfo, propertyTable: Dictionary): Tween`
>
> Creates a new `Tween` given the object whose properties are to be tweened.

#### Parameters

- `instance: Instance` — The `Instance` whose properties are to be tweened.
- `tweenInfo: TweenInfo` — The `TweenInfo` to be used.
- `propertyTable: table` — A dictionary of properties, and their target values, to be tweened.

## Testing Notes

`TweenService.Create` and its returned Tween surface were revalidated in
Vortex Studio 0.8.1.

`Create` returned a Tween in both `Script` and `LocalScript` when given an
unparented `Part`, `TweenInfo.new(0.1)`, and `{ Transparency = 0.5 }`.
