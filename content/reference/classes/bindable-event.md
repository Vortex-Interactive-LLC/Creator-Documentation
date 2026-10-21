---
title: BindableEvent
description: A partially exposed local-event instance.
---

## Runtime support

`BindableEvent` can be constructed in Vortex Studio 0.3.4 in both `Script` and
`LocalScript`. It exposes an `Event` table.

However, the instance has no `Fire` method, scripts cannot fire that signal.
It therefore cannot currently be used as an in-process event bus.

```lua
local event = Instance.new("BindableEvent")
print(event.Event) -- signal table
print(event.Fire)  -- nil
event:Destroy()
```
