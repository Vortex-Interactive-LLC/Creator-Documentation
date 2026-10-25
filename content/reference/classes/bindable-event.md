---
title: BindableEvent
description: A partially exposed local-event instance.
---

<!--
Debris
Revision 1

-->

## Summary

<details>
<summary><b>Methods</b></summary>
Methods of `BindableEvent`.
<br><br>

* [Fire](#fire)

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `BindableEvent`.
<br><br>

* [Event](#event): `Connection`

</details>

## Overview

`BindableEvent` is an instance that enables an event within scripts at the same context level; server **or** client.

## Methods

### Fire

> `Fire(arguments: Tuple)`
>
> Fires `BindableEvent` that enables its signal. Returns nothing.

#### Parameters

- `arguments`: `Tuple` — a tuple consisting of variables of any class.

## Signals

### Event

> `Event(arguments: Tuple): Connection`
>
> The signal fires when any script calls [Fire](#Fire) method for this `BindableEvent`. Returns `Connection`.

#### Parameters

- `arguments`: `Tuple` — the parameters sent through [Fire](#Fire).

## Testing Notes

The exposed method surface was revalidated in Vortex Studio 0.8.1; detailed
method behavior may differ in later releases.

`ClassName` of `Connection` is `RBXScriptSignal`.
