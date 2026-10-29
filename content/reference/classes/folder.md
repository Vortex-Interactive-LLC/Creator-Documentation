---
title: Folder
description: A general-purpose container for instances.
---

## Runtime support

`Folder` can be constructed in both `Script` and `LocalScript`. It exposes the generic instance and hierarchy methods, including `FindFirstChild`, `GetChildren`, `GetDescendants`, and `WaitForChild`.

## Hierarchy

Instances parented to a Folder become its children: `child.Parent == folder` is `true`, and `FindFirstChild`, `GetChildren()`, `GetDescendants()`, and `WaitForChild` all find them. A Folder can itself be parented to `Workspace` or another container.

Folders are used to organize instances; they have no other behavior.
