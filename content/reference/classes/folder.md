---
title: Folder
description: A general-purpose container for instances.
---

## Runtime support

`Folder` can be constructed in Vortex Studio 0.3.4 in both `Script` and
`LocalScript`. It exposes the generic instance and hierarchy methods,
including `FindFirstChild`, `GetChildren`, `GetDescendants`, and
`WaitForChild`.

## Hierarchy limitation

A detached Folder cannot form an observable hierarchy at runtime. Assigning a
temporary Part's `Parent` to the Folder causes  `child.Parent == folder` to remain false;
`FindFirstChild` returns `nil`; `GetChildren()` and `GetDescendants()` return
empty tables; and `WaitForChild` does not return the Part.

Likewise, assigning the Folder's `Parent` to `Workspace` causes the parent comparison to 
remain false and does not make the Folder visible through Workspace lookups or
`GetChildren()`.

Use Folders created in the editor for organization. Do not rely on a script to
create or populate a runtime Folder hierarchy.
