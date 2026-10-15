---
title: BoolValue
description: An unsupported Roblox-compatible boolean value container.
---

## Runtime support

`Instance.new("BoolValue")` is not supported in Vortex Studio 0.3.4. It fails
in both `Script` and `LocalScript` with an "unable to create instance" error.

Use a regular Lua boolean or an [`IntValue`](./int-value.md)
with a documented `0`/`1` convention, when you need to store boolean state.
