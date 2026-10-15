---
title: ServerScriptService
description: The service surface for editor-authored server Scripts.
---

## Summary

`ServerScriptService` is a service used to store and run editor-authored server Scripts.
Scripts placed here execute on the server and are not intended to run on the client.

## Runtime support

`game:GetService("ServerScriptService")` is available in both Script and
LocalScript contexts in Vortex Studio 0.3.4. It exposes `FindFirstChild`,
`GetChildren`, and `WaitForChild`.

Runtime-created Scripts do not become observable children when assigned to
this service: the parent comparison and `FindFirstChild` both fail, and
`GetChildren()` does not include the temporary Script. Place server Scripts in
the editor instead of trying to create or attach them through code.
