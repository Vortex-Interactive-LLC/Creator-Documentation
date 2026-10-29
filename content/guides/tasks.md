---
title: Tasks
description: Schedule work with Vortex task helpers.
---
> [!Summary]
> Tasks provide timing helpers for scheduling work, delaying logic, and running asynchronous operations. In Vortex, `task.spawn`, `task.defer`, `task.delay`, and `task.wait` let you control when code runs.

## Available helpers

Vortex Studio 0.3.4 provides `task.spawn`, `task.defer`, `task.delay`, and `task.wait` in both Script and LocalScript. See the full [`task`](/content/reference/globals/task.md) reference.

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

`task.spawn` completed during the scheduling call in the tested runtime. `task.defer` and `task.delay(0, callback)` remained pending after the first `task.wait()` and completed during the second scheduler cycle. `task.wait()` returns an elapsed-time number.

`task.cancel`, `task.desynchronize`, and `task.synchronize` are unavailable.
