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

`Signal.new` was available in the earlier 0.3.4 tests, but the global `Signal` was `nil` in a Vortex Studio 0.3.8 server Script. Use an engine-owned signal, such as `Part.Changed`, in the current release.

## Vortex Studio 0.3.4 notes

`Connect`, `Once`, `Wait`, and `Fire` were revalidated on `Part.Changed` in both `Script` and `LocalScript`; a manually fired signal delivered once before disconnect and not afterward. `ConnectParallel` remains absent.

In a LocalScript, `UserInputService.InputBegan:Once` and `:Wait` both delivered the same right-mouse-button input. A normal Script still has no `UserInputService`.

The `Part` attribute/property-change signals used in the examples are connectable, but mutating the corresponding attribute or property still did not deliver callbacks in 0.3.4.

In 0.3.4, lowercase `connect` and `fire` work on `Part.Changed`, and `Signal.new` creates a standalone signal whose `Connect` callback receives a manually fired argument. This was confirmed in both Script and LocalScript.

In Vortex Studio 0.3.8, an engine-owned `Part.Changed` signal still exposed `Connect`, `Fire`, `Once`, and `Wait`. A manual `Fire("yes")` reached a connected callback once; after `Disconnect()`, a second fire did not reach it. The global `Signal` constructor was `nil` in the tested server Script.
