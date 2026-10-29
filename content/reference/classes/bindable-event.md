---
title: BindableEvent
description: A partially exposed local-event instance.
---

## Summary

A `BindableEvent` is a custom event that scripts on the same side of the game can fire and listen to. It can be constructed in both `Script` and `LocalScript`, and cannot send anything between the client and the server. Use a [`RemoteEvent`](./remote-event.md) for that.

## Members

- `Event` - a [`Signal`](../datatypes/signal.md). Connect to it to receive the arguments passed to `Fire`.
- `Fire(...)` - fires `Event`, passing the arguments to every connected function.

```lua
local event = Instance.new("BindableEvent")

event.Event:Connect(function(a, b)
    print(a, b) --> 1 2
end)

event:Fire(1, 2)
event:Destroy()
```
