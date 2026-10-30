---
title: ModuleScript
description: A non-executable runtime module shell.
---

## Runtime support

`ModuleScript` can be constructed in both `Script` and `LocalScript` contexts. `Source`, `Disabled`, and `RunContext` read as `nil`, and assigning `Source` is rejected, so a ModuleScript created at runtime cannot hold code.

Modules written in the editor are loaded with the global `require` function.