---
title: BindableFunction
description: A function one script can define and another script on the same side can call.
---

## Summary

A `BindableFunction` lets scripts on the same side of the game, both on the server or both on the client, call a function in another script and get its return values. It cannot call across the client and the server. Use a [`RemoteFunction`](./remote-function.md) for that.

```lua
local bf = Instance.new("BindableFunction")

bf.OnInvoke = function(a, b)
    return a + b, "done"
end

print(bf:Invoke(2, 3)) --> 5 done
```

## Members

- `OnInvoke` - the function that runs when `Invoke` is called. Assign it before invoking;
- `Invoke(...)` - calls `OnInvoke` with the arguments and returns what it returns.

An error inside `OnInvoke` is raised from the `Invoke` call, so wrap it in `pcall` to handle it. Calling `Invoke` on a `BindableFunction` that has no `OnInvoke` does not return.
