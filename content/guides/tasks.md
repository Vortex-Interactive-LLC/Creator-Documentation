---
title: Tasks
description: Schedule work with Vortex task helpers.
---
> [!Summary]
> Tasks provide timing helpers for scheduling work, delaying logic, and running asynchronous operations. In Vortex, `task.spawn`, `task.defer`, `task.delay`, and `task.wait` let you control when code runs.

## Available helpers

Vortex provides `task.spawn`, `task.defer`, `task.delay`, `task.wait`, and `task.cancel` in both Script and LocalScript. See the full [`task`](../reference/globals/task.md) reference.

```lua
task.spawn(function()
    print("runs immediately in the current scheduling call")
end)

task.defer(function()
    print("runs on a later scheduler cycle")
end)

task.delay(1, function()
    print("runs after approximately one second")
end)
```

## Scheduling behavior

`task.spawn` runs the function immediately, before the calling code continues. `task.defer` and `task.delay(0, callback)` run on the next scheduler cycle, before a following `task.wait()` returns. `task.wait()` returns the elapsed time in seconds.

`task.cancel(thread)` cancels a thread returned by `task.delay` before it runs. `task.desynchronize` and `task.synchronize` are not available.
