---
title: ModuleScript
description: A non-executable runtime module shell.
---

## Runtime support

`ModuleScript` can be used in Vortex Studio 0.8.1 in both `Script` and
`LocalScript` contexts. `Source`, `Disabled`, and `RunContext` read as `nil`, and assigning
`Source` is rejected.

## Overview

A universal script that returns exactly one value, usually a table of functions, to used by other scripts.

ModuleScripts are typically placed in `ReplicatedStorage` so that they are visible in both run contexts.

## Code Samples

To activate a `ModuleScript`, you need to specify the path to it using the `require` function. 
```luau
local moduleScript = require(game:GetService('ReplicatedStorage').ModuleScript)
```
