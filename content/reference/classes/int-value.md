---
title: IntValue
description: A detached integer value container.
---

<!--
Debris
Revision 1

-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `IntValue`.
<br><br>

* [Value](#value): `number`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `IntValue`.
<br><br>

* [Changed](#changed): `Connection`

</details>

## Overview

`IntValue` is an instance that contains and modifies a `number` value.

## Properties

### Value

> `IntValue.Value: number`
>
> `number` value.

## Signals

### Changed

> `Changed(value: number): Connection`
>
> Fires whenever the `Value` property of `IntValue` changes.

#### Parameters

- `value: number` — new `Value` property of `IntValue`

## Testing Notes

The exposed method surface was revalidated in Vortex Studio 0.8.1; detailed
method behavior may differ in later releases.

`ClassName` of `Connection` is `RBXScriptSignal`
