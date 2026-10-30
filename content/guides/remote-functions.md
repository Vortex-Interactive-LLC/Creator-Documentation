---
title: Remote Functions
description: Current RemoteFunction support and limitations in Vortex.
---
> [!Summary]
> RemoteFunctions let a client request information or a result from the server. Use them for request-response flows. Instance arguments are not supported.

## Current support

An editor-authored [`RemoteFunction`](../reference/classes/remote-function.md) in [`ReplicatedStorage`](../reference/classes/replicated-storage.md) exposes `InvokeServer` to a LocalScript. A server Script can assign `OnServerInvoke`.

Instance arguments are not supported: invoking with `LocalPlayer` fails before delivery with an "Instances cannot be sent" runtime error.

## Practical guidance

Prefer an editor-authored [`RemoteEvent`](../reference/classes/remote-event.md) with primitive payloads when one-way client-to-server communication is sufficient. The `OnServerEvent` handler of a `RemoteEvent` receives the `Player` who fired it as its first argument.
