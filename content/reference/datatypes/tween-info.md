---
title: TweenInfo
description: Information of a tween
---

<!--
Expanded by CNK (Vortex IG. CNK) on Aug 30th, 2026 based on actual code.
-->

## Summary

<details>
<summary><b>Constructors</b></summary>

Constructors of a `TweenInfo`.
<br><br>

* [new(time: `Number?`, easingStyle: `Enum.EasingStyle?`, easingDirection: `Enum.EasingDirection?`, repeatCount: `Number?`, reverses: `Boolean?`, delayTime: `Number?`)](#tweeninfonewtime-number-easingstyle-enumeasingstyle-easingdirection-enumeasingdirection-repeatcount-number-reverses-boolean-delaytime-number): `TweenInfo`

</details>

<details>
<summary><b>Properties</b></summary>

Properties of a `TweenInfo`.
<br><br>

* [Time](#time): `Number`
* [EasingStyle](../globals/enum.md#easingstyle): `Enum.EasingStyle`
* [EasingDirection](../globals/enum.md#easingdirection): `Enum.EasingDirection`
* [RepeatCount](#repeatcount): `Number`
* [Reverses](#reverses): `Boolean`
* [DelayTime](#delaytime): `Number`

</details>

## Constructors

### TweenInfo.new(time: `Number?`, easingStyle: `Enum.EasingStyle?`, easingDirection: `Enum.EasingDirection?`, repeatCount: `Number?`, reverses: `Boolean?`, delayTime: `Number?`)

> `TweenInfo`
>
> Returns a `TweenInfo` data container to be fed into [TweenService](../classes/tween-service.md).
> 
> Note that `time` is in seconds.
> 
> All constructor parameters are optional, so not everything has to be specified; note the following defaults:
> * `TweenInfo.Time` = `1`
> * `TweenInfo.EasingStyle` = `Enum.EasingStyle.Quad`
> * `TweenInfo.EasingDirection` = `Enum.EasingDirection.Out`
> * `TweenInfo.RepeatCount` = `0`
> * `TweenInfo.Reverses` = `false`
> * `TweenInfo.DelayTime` = `0`

<br/>

## Properties

### Time

> `Number`
>
> Duration for the tween, in seconds.

<br/>

### EasingStyle

> `Enum.EasingStyle`
>
> Easing style for the tween.

<br/> 

### EasingDirection 

> `Enum.EasingDirection`
>
> Direction in which the tween should execute.
<br/>

### RepeatCount

> `Number`
>
> Number of times the tween repeats.
> 
> Note that if repeat count is `-1` it will repeat forever.

> Set `repeatCount` to `-1` to repeat forever.

<br/>

### Reverses 

> `Boolean`
>
> Whether the tween should reverse to the starting value once it reaches its target.

<br/>

### DelayTime 

> `Number`
>
> Time before the tween begins, in seconds.
<br/>

## Constructors

### new

> `TweenInfo`
>
> `TweenInfo.new(time: Number, easingStyle: Enum.EasingStyle, easingDirection: Enum.EasingDirection, repeatCount: Number, reverses: Boolean, delayTime: Number)`
>
> Creates a TweenInfo value that configures a Tween.

#### Parameters

- `time`: `Number` — the duration in seconds.
- `easingStyle`: `Enum.EasingStyle` — the easing curve.
- `easingDirection`: `Enum.EasingDirection` — the easing direction.
- `repeatCount`: `Number` — the number of repeats; `-1` repeats forever.
- `reverses`: `Boolean` — whether each repeat reverses direction.
- `delayTime`: `Number` — the delay before playback begins, in seconds.

## Testing Notes

`TweenInfo.new(0.1, Enum.EasingStyle.Linear, Enum.EasingDirection.In, 0, false, 0)` returns a TweenInfo table in both `Script` and `LocalScript`.

`repeatCount = -1` is treated as an infinite repeat count.
