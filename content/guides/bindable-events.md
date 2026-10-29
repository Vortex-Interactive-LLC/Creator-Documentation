---
title: Bindable Events
description: Current BindableEvent support in Vortex Studio.
---
> [!Summary]
> BindableEvents let scripts signal each other within the same side of the game (server to server, or client to client). Connect to `Event` and emit with `Fire`. They never cross the client-server boundary; use a [`RemoteEvent`](../reference/classes/remote-event.md) for that.

A `BindableEvent` exposes an `Event` signal and a `Fire(...)` method. Arguments passed to `Fire` are delivered to every function connected to `Event`.

```lua
local event = Instance.new("BindableEvent")

event.Event:Connect(function(a, b)
    print(a, b) --> 1 2
end)

event:Fire(1, 2)
```

A BindableEvent cannot send anything between the client and the server.
