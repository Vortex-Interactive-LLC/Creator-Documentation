---
title: Remote Functions
description: Current RemoteFunction support and limitations in Vortex.
---
> [!Summary]
> RemoteFunctions let a client request information or a result from the server. Use them for request-response flows, but note that Instance arguments and some runtime behaviors are still limited in Vortex.

## Current support

An editor-authored [`RemoteFunction`](../reference/classes/remote-function.md) in `ReplicatedStorage` exposes `InvokeServer` to a LocalScript. A server Script can assign `OnServerInvoke`.

Instance arguments are not supported: invoking with `LocalPlayer` fails before delivery with an "Instances cannot be sent" runtime error. A successful primitive request-response round trip has not yet been established in Vortex Studio 0.3.4.

## Practical guidance

Do not use RemoteFunctions for critical gameplay paths yet. Prefer an editor-authored [`RemoteEvent`](../reference/classes/remote-event.md) with primitive payloads when one-way client-to-server communication is sufficient RemoteEvent delivery has been observed; the sender value received by the server is a numeric identifier, not a Player instance.
