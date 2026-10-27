---
title: StringValue
description: A detached string value container.
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `StringValue`.
<br><br>

* [Value](#value): `boolean`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `StringValue`.
<br><br>

* [Changed](#changed): `Connection`

</details>

## Overview

`StringValue` is an instance that contains and modifies a `string` value.

## Properties

### Value

> `StringValue.Value: string`
>
> `string` value.

## Signals

### Changed

> `Changed(value: string): Connection`
>
> Fires whenever the `Value` property of `StringValue` changes.

#### Parameters

- `value: string` — new `Value` property of `StringValue`.

## Testing Notes

The exposed method surface was revalidated in Vortex Studio 0.8.1; detailed
method behavior may differ in later releases.

`ClassName` of `Connection` is `RBXScriptSignal`.
