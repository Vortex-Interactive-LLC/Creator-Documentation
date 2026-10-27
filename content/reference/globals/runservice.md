---
title: RunService
description: Provides runtime-context helpers and a per-frame heartbeat signal.
---

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of `RunService`.
<br><br>

* [IsClient](#isclient): `Boolean`
* [IsServer](#isserver): `Boolean`
* [IsStudio](#isstudio): `Boolean`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `RunService`.
<br><br>

* [Heartbeat](#heartbeat): `Connection`

</details>

## Overview

`RunService` is available through `game:GetService("RunService")`.

## Methods

### IsClient

> `RunService:IsClient(): boolean`
>
> Returns whether the current script runs in a client context.

### IsServer

> `RunService:IsServer(): boolean`
>
> Returns whether the current script runs in a server context.

### IsStudio

> `RunService:IsStudio(): boolean`
>
> Returns whether the current runtime is Vortex Studio.

## Signals

### Heartbeat

> `Heartbeat(deltaTime: number)`
>
> Fires once per runtime update with the elapsed time since the previous update, right after the frame’s physics are finished.

#### Parameters

- `deltaTime`: `number` — elapsed time in seconds since the previous heartbeat.

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later
releases.

`IsClient()` returned `true` in a `LocalScript` and `false` in a `Script`.
`IsServer()` returned the inverse. `IsStudio()` returned `true` in both
contexts.

`Heartbeat` supports `Connect`, `Once`, and `Wait`. Its observed `deltaTime`
varied between updates, so it should not be treated as a fixed interval. This event works in both contexts.

The `Stepped` and `RenderStepped` events exist, but they are equivalent to `Heartbeat` though the latter can only be triggered only in local scripts.
