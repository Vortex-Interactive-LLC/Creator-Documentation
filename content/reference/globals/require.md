---
title: require
description: Loads a ModuleScript and returns what it returns.
---

`require(module)` runs a [`ModuleScript`](../classes/modulescript.md) the first time it is required and returns the single value the module returned. Later calls return the same value.

```lua
local Counter = require(game.ReplicatedStorage.Counter)
Counter.increment()
```

`module` must be a `ModuleScript` instance. Passing a string, `nil`, or any other instance raises an error. The module must return exactly one value, and an error inside the module is raised in the script that called `require`.

See the [ModuleScripts guide](../../guides/modulescripts.md).
