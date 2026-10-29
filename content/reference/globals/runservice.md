---
title: RunService
description: Provides runtime-context helpers and a per-frame heartbeat signal.
---

`RunService` is available through `game:GetService("RunService")`.

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

* [Heartbeat](#heartbeat): [`Signal`](../datatypes/signal.md)

</details>

## Methods

### IsClient

> `Boolean`
>
> `RunService:IsClient()`
>
> Returns whether the current script runs in a client context.

<br/>

### IsServer

> `Boolean`
>
> `RunService:IsServer()`
>
> Returns whether the current script runs in a server context.

<br/>

### IsStudio

> `Boolean`
>
> `RunService:IsStudio()`
>
> Returns whether the current runtime is Vortex Studio.

<br/>

## Signals

### Heartbeat

> [`Signal`](../datatypes/signal.md)
>
> `RunService.Heartbeat`
>
> Fires once per runtime update with the elapsed time since the previous update.

#### Parameters

- `deltaTime`: `Number` — elapsed time in seconds since the previous heartbeat.

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later releases.

`IsClient()` returned `true` in a `LocalScript` and `false` in a `Script`. `IsServer()` returned the inverse. `IsStudio()` returned `true` in both contexts.

`Heartbeat` supports `Connect`, `Once`, and `Wait`. Its observed `deltaTime` varied between updates, so it should not be treated as a fixed interval.
