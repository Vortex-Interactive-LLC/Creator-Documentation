---
title: task
description: Runtime task scheduling helpers.
---

## Summary

<details>
<summary><b>Functions</b></summary>
Runtime task scheduling helpers.
<br><br>

- [defer](#defer): queues a callback for a later scheduler cycle.
- [delay](#delay): queues a callback after a duration.
- [spawn](#spawn): runs a callback as soon as the scheduler can run it.
- [wait](#wait): yields the current thread until the scheduler resumes it.

</details>

## Functions

### defer()

```luau
task.defer(callback: Function, ...: any)
```

Queues `callback` to run in a later scheduler cycle without yielding the calling thread. Extra arguments are passed to `callback`.

#### Parameters

- `callback`: `Function` — the function to schedule.
- `...`: `any` — optional arguments passed to `callback`.

### delay()

```luau
task.delay(duration: Number, callback: Function, ...: any)
```

Queues `callback` to run after `duration` seconds. Extra arguments are passed to `callback`.

#### Parameters

- `duration`: `Number` — the delay, in seconds.
- `callback`: `Function` — the function to schedule.
- `...`: `any` — optional arguments passed to `callback`.

### spawn()

```luau
task.spawn(callback: Function, ...: any)
```

Schedules `callback` to run as soon as possible without yielding the calling thread. Extra arguments are passed to `callback`.

#### Parameters

- `callback`: `Function` — the function to schedule.
- `...`: `any` — optional arguments passed to `callback`.

### wait()

```luau
task.wait(duration: Number?): Number
```

Yields the current thread until the scheduler resumes it, or until at least `duration` seconds have elapsed when a duration is supplied. Returns the elapsed time.

#### Parameters

- `duration`: `Number?` — an optional duration to wait, in seconds.

## Availability

`task.defer`, `task.delay`, `task.spawn`, `task.wait`, and `task.cancel` are available in both `Script` and `LocalScript`.

## Notes

`task.spawn` runs the callback immediately, before the calling code continues. `task.defer` and `task.delay(0, callback)` run on the next scheduler cycle, before a following `task.wait()` returns. `task.wait()` returns the elapsed time in seconds.

`task.cancel(thread)` cancels a thread returned by `task.delay` before it runs. `task.desynchronize` and `task.synchronize` are not exposed.
