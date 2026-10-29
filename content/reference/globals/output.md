---
title: Output
description: Print and diagnose script output in Vortex Studio.
---

## print

`print` is available in both Script and LocalScript in Vortex Studio 0.3.4. It accepts multiple values and formats Vortex values such as `Vector3` for the Output panel. It returns `nil`.

```lua
print("position", true, 42, Vector3.new(1, 2, 3))
```

Output is labelled with the executing script type while the game is running. Use your own prefixes when several scripts emit related diagnostics.

## Warnings and caught errors

`warn` is unavailable. `error` and `assert` are available; when called inside `pcall`, they return `false` and an error string containing the generated script identifier, line number, and message.

```lua
local ok, message = pcall(function()
    error("something went wrong")
end)

print(ok, message)
```

This page only describes caught failures. An uncaught error ends the current script path and should be used deliberately when debugging.
