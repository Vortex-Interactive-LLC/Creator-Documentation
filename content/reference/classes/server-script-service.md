---
title: ServerScriptService
description: The service surface for editor-authored server Scripts.
---

## Summary

`ServerScriptService` is a service used to store and run editor-authored server Scripts. Scripts placed here execute on the server and are not intended to run on the client.

## Runtime support

`game:GetService("ServerScriptService")` is available in both Script and LocalScript contexts. It exposes `FindFirstChild`, `GetChildren`, and `WaitForChild`.

Place server Scripts in the editor. A `Script` created at runtime has no `Source`, so it cannot run code.
