---
title: Bindable Events
description: Current BindableEvent support in Vortex Studio.
---
> [!Summary]
> BindableEvents let scripts signal local notifications and state changes within the same runtime. In Vortex, they are available for scripting, but their fire behavior is limited and should not be used for authoritative game communication.

`BindableEvent` can be created and exposes an `Event` table in both Scripts and LocalScripts. However, the method required to emit an event, `BindableEvent:Fire(...)`, is not available in Vortex Studio 0.3.4.

As a result, BindableEvents cannot currently be used for communication between scripts. Use a shared state mechanism or an authored [`RemoteEvent`](../reference/classes/remote-event.md) when communication needs to cross the client-server boundary.