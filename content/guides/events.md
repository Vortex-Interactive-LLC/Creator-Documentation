---
title: Events
description: Connect to and handle runtime signals in Vortex.
---
> [!Summary]
> Signals let you respond to runtime events by connecting callbacks to a `Signal`. Use `:Connect` to listen for updates, `:Once` or `:Wait` for one-time handling, and disconnect listeners when they are no longer needed.

## Signals

Events are represented by [`Signal`](/content/reference/datatypes/signal.md) values. Connect a callback with `:Connect`, keep the returned [`Connection`](/content/reference/datatypes/connection.md), and disconnect it when the listener is no longer needed.

```lua
local connection = game:GetService("RunService").Heartbeat:Connect(function(deltaTime)
    print(deltaTime)
end)

connection:Disconnect()
```

`Once` and `Wait` are also available. `ConnectParallel` is not exposed.

## Delivery limits

Manual `Signal:Fire(...)` delivery works for standalone signals and other supported signals. Some instance change signals are only partially implemented: they can be connected, but do not fire when the corresponding property or attribute is changed. `Part.Changed`, user input, Humanoid health-related signals, and remote-event signals each need to be treated according to their documented runtime behavior.

Do not treat a connectable signal as proof that a producer exists. Confirm that the specific event delivers in the context where your code runs.
