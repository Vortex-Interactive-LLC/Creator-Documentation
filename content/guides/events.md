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

Manual `Signal:Fire(...)` delivery works for standalone signals and other supported signals. Instance change signals (`Changed`, `GetPropertyChangedSignal`, `GetAttributeChangedSignal`) fire for instances that are parented into the game and do not fire for instances that have no parent. Some signals only exist in one context: for example, [`UserInputService`](../reference/classes/user-input-service.md) is only available in a LocalScript, and `OnServerEvent` only fires on the server.

See the reference page for each class to confirm which context an event fires in.
