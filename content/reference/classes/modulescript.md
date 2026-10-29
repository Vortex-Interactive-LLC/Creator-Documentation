---
title: ModuleScript
description: A non-executable runtime module shell.
---

## Runtime support

`ModuleScript` can be constructed in Vortex Studio 0.3.4 in both `Script` and
`LocalScript` contexts, but it cannot be used as a functional module at
runtime. `Source`, `Disabled`, and `RunContext` read as `nil`, and assigning
`Source` is rejected.

The global `require` function is unavailable. Consequently, a runtime-created
ModuleScript cannot provide shared executable code. Assigning it to
[`ReplicatedStorage`](./replicated-storage.md) does
not establish an observable parent-child relationship.
