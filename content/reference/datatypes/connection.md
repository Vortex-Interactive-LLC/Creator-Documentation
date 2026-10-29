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

This uses an engine-owned Signal. The standalone `Signal.new` constructor was not available in the tested Vortex Studio 0.3.8 server Script.

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later releases.

Connections are represented as tables. The lowercase `disconnect` alias is also exposed; this reference uses the canonical `Disconnect` name.

In both Script and LocalScript, `Connected` began as `true`, a manually fired signal delivered its callback once, and `Disconnect()` changed `Connected` to `false` and prevented later delivery. The lowercase `disconnect()` alias has the same effect.

The engine-owned Signal example was revalidated in a Vortex Studio 0.3.8 server Script. The callback ran for the first manual fire, `Disconnect()` made `Connected` false, and a second fire did not run the callback.
