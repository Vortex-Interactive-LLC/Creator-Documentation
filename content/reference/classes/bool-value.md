---
title: BoolValue
description: A detached boolean value container.
---

<!--
Debris
Revision 1

-->

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `BoolValue`.
<br><br>

* [Value](#value): `boolean`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `BoolValue`.
<br><br>

* [Changed](#changed): `Connection`

</details>

## Overview

`BoolValue` is an instance that contains and modifies a `boolean` value.

## Properties

### Value

> `BoolValue.Value: boolean`
>
> `boolean` value

## Signals

### Changed

> `Changed(value: boolean): Connection`
>
> Fires whenever the `Value` property of `BoolValue` changes.

#### Parameters

- `value: boolean` — new `Value` property of `BoolValue`

## Testing Notes

The exposed method surface was revalidated in Vortex Studio 0.8.1; detailed
method behavior may differ in later releases.

ClassName of `Connection` is `RBXScriptSignal`
