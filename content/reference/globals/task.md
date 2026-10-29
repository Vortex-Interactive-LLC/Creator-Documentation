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

## Verified runtime compatibility

`task.defer`, `task.delay`, `task.spawn`, and `task.wait` were present in both `Script` and `LocalScript` in Vortex Studio 0.3.4.

The initial capability probe verifies function presence; the dedicated behavior probe records the scheduling details below.

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later releases.

`task.cancel`, `task.desynchronize`, and `task.synchronize` are not exposed. `task.spawn` completes during the scheduling call itself. `task.defer` and `task.delay(0, callback)` are still pending after one `task.wait()` and complete during the second wait cycle. `task.wait()` returns a number.
