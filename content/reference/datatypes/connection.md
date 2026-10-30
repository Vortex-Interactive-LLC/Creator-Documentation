---
title: Connection
description: Represents a callback connected to a Signal.
---

A `Connection` is returned by [`Signal:Connect`](./signal.md#connect) or [`Signal:Once`](./signal.md#once). It can be used to stop the callback from receiving future signal fires.

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of a `Connection`.
<br><br>

* [Connected](#connected): `Boolean`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of a `Connection`.
<br><br>

* [Disconnect](#disconnect)

</details>

## Properties

### Connected

> `Boolean`
>
> Whether the connection is currently active.

<br/>

## Methods

### Disconnect

> `connection:Disconnect()`
>
> Disconnects the callback. Future signal fires no longer invoke it, and `Connected` becomes `false`.

## Example

Keep the returned Connection when the callback should stop later:

```luau
local part = workspace:FindFirstChild("Baseplate")
if not part then
    return
end

local signal = part.Changed
local connection = signal:Connect(function(message)
    print(message)
end)

signal:Fire("received")
connection:Disconnect()
signal:Fire("not received")

print(connection.Connected) -- false
```

This uses an engine-owned Signal; there is no standalone `Signal.new` constructor.

## Notes

Connections are represented as tables. The lowercase `disconnect` alias is also exposed; this reference uses the canonical `Disconnect` name.

In both Script and LocalScript, `Connected` begins as `true`. `Disconnect()` changes `Connected` to `false` and prevents later delivery to the callback.
