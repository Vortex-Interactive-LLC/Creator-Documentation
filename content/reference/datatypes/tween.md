---
title: Tween
description: An object used to smoothly change properties of an instance over a period of time. Tweens can be used to animate properties such as position, size, transparency, color, and other supported values. Constructed with `TweenService`.
---

<!--
Written by CNK (Vortex IG. CNK) on Aug 30th, 2026 based on actual code.
-->

## Summary

> If you are looking to construct a tween, reference [TweenService](../classes/tween-service.md). Then come back here after your tween has been created.

<details>
<summary><b>Properties</b></summary>

Properties of a `Tween`.
<br><br>

* [Instance](#instance): `Instance`
* [PlaybackState](#playbackstate): `Enum.PlaybackState`

</details>

<details>
<summary><b>Methods</b></summary>

Methods of a `Tween`.
<br><br>

* [Play()](#play): `nil`
* [Pause()](#pause): `nil`
* [Cancel()](#cancel): `nil`

</details>
<details>
<summary><b>Events</b></summary>
<br><br>

* [Completed](#completedplaybackstate-enumplaybackstate)

</details>

## Properties


### Instance

> `Instance`
>
> The object which the tween would act upon.

<br/>

### PlaybackState

> `Enum.PlaybackState`
>
> The current state of the tween.
> 
> #### Examples:
> * `Enum.PlaybackState.Playing` - When the tween is active.
> * `Enum.PlaybackState.Cancelled` - If the tween was cancelled before it finished.
> * Reference `Enum.PlaybackState` for more states.

<br/>

## Methods


### Play()


> Triggers the tween to start/continue playing.

<br/>

### Pause()

> Pauses the tween where it is at and will continue once `Tween:Play()` is called again.

<br/>

### Cancel()

> Stops the tween where it is at and resets the tween to the start position.

<br/>

## Events

### .Completed(playbackState: `Enum.PlaybackState`)

> Fires when the tween finishes, whether it completed naturally or was stopped early with [`Cancel()`](#cancel).
>
> The connected function receives one argument: the resulting `Enum.PlaybackState`, either `Completed` or `Cancelled`.
>
> ```luau
> -- Example of the `Completed` signal being used.
> myTween.Completed:Connect(function(playbackState)
>     if playbackState == Enum.PlaybackState.Completed then
>         print("Tween finished naturally")
>     end
> end)
> ```

<br/>
