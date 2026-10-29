---
title: Signal
description: An object that runs connected functions in a specific way.
---

<!--
Signal
Revision 1.0

Written by TheJustDare on August 30th, 2026
-->

## Summary

<details>
<summary><b>Methods</b></summary>

* [Connect()](#connect): `Connection`
* [Fire()](#fire): `nil`
* [Once()](#once): `Connection`
* [Wait()](#wait): `any`
</details>

## Overview

[Signal](./signal.md) is a data type that is used in user-defined functions, otherwise known as **listeners**, to trigger when something happens in the game. \
 The [Signal](./signal.md) might also happen to pass arguments to each listener depending on which event it is.

## Methods

### Connect()

Connects the given function and creates a new [Connection](./connection.md).

```lua
local part = workspace:FindFirstChild("Baseplate")
if not part then
    return
end

local connection = part.Changed:Connect(function(message)
    print(message)
end)

part.Changed:Fire("changed")
```

<br>

### Fire()

Synchronously invokes connected callbacks with the supplied arguments.

```lua
local part = workspace:FindFirstChild("Baseplate")
if not part then
    return
end

local signal = part.Changed
signal:Connect(function(message)
    print(message)
end)
signal:Fire("Hello")
```

<br>

### Once()

Connects the given function and creates a new [Connection](./connection.md). \
`Once` will run the function only **once**, unlike the other methods.

```lua
local part = workspace:FindFirstChild("Baseplate")
if not part then
    return
end

part.Changed:Once(function(message)
    print(message)
end)

part.Changed:Fire("first")
part.Changed:Fire("second") -- the callback does not run again
```

### Wait()

Yields the current thread until the `Signal` fires. `Wait()` returns arguments passed by the signal.

### new()

There is no global `Signal` constructor, so `Signal.new` is not available. Use an engine-owned signal, such as `Part.Changed`.

## Notes

`Connect`, `Once`, `Wait`, and `Fire` work on engine-owned signals such as `Part.Changed`, and the lowercase aliases `connect` and `fire` are also available. A signal that is fired manually delivers to its connected functions, and stops delivering to a function once it is disconnected. `ConnectParallel` is not available.

The `Part` and value-object change signals (`Changed`, `GetPropertyChangedSignal`, `GetAttributeChangedSignal`) fire when the property or attribute changes on an instance that is parented into the game.

In a LocalScript, `UserInputService.InputBegan:Once` and `:Wait` deliver the next input. A normal Script has no `UserInputService`.
