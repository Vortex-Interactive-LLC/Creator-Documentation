---
title: ModuleScripts
description: Share code between scripts with ModuleScripts and require.
---
A `ModuleScript` holds code that other scripts can load with `require`. Use one when several scripts need the same functions or data.

## Writing and requiring a module

A module returns exactly one value, usually a table.

```luau
-- ModuleScript named "Counter"
local Counter = {}
Counter.count = 0

function Counter.increment()
    Counter.count += 1
    return Counter.count
end

return Counter
```

```luau
-- Script
local Counter = require(game.ReplicatedStorage.Counter)

print(Counter.increment()) --> 1
print(Counter.increment()) --> 2
```

A module can also return a function. Then the result of `require` is the function, and you call it directly.

```luau
-- ModuleScript named "Double"
return function(x)
    return x * 2
end
```

```luau
local double = require(game.ReplicatedStorage.Double)
print(double(21)) --> 42
```

## Calling the result

`require` returns whatever the module returned. If it returned a table, call the functions inside it. Calling the table itself fails with `attempt to call a table value`.

```luau
local Counter = require(game.ReplicatedStorage.Counter)

Counter.increment() -- correct
Counter()           -- error: attempt to call a table value
```

## Behaviour

- A module runs once per script runtime, the first time it is required. Later `require` calls return the same value, so `require(m) == require(m)` is `true` and state stored in the table is shared.
- Server scripts and local scripts each load their own copy. A module required on the server and on the client does not share state between them.
- A module must return exactly one value. Returning none, or more than one, raises an error.
- An error inside a module propagates to the script that required it. Wrap `require` in `pcall` to handle it.
- `require` only accepts a `ModuleScript` instance. Passing a string, `nil`, or another instance raises an error.
- A module cannot require itself, directly or through a cycle.

> [!NOTE]
> Inside a module, `script` is the module itself, so `script.Parent.Helper` finds a sibling module.

See [`require`](../reference/globals/require.md) and the [`ModuleScript`](../reference/classes/modulescript.md) reference.
