---
title: Script
description: An editor-authored server execution asset.
---

## Runtime support

`Script` can be created in both `Script` and `LocalScript` contexts. The temporary instance exposes its `ClassName` and `Name`, but `Source`, `Disabled`, and `RunContext` read as `nil`.

`Source` is not settable. A runtime-created Script therefore cannot be given code and cannot become an executable server script.

Use an editor-authored Script to run server-side code. Within one, the global `script` refers to the current Script instance.
