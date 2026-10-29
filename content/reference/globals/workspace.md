---
title: workspace
description: Keyword representing the global Workspace root
---

<!-- 
workspace
Revision 1.1

Written by mezz-source on August 29th, 2026
-->

The `workspace` keyword represents game's root [Workspace](../classes/workspace.md) service, which contains all physical models, parts, and other [Instances](../classes/instance.md) that can exist inside of it.

It can be used to index specific [Instances](../classes/instance.md) or to collect objects quickly, in respect to the server or client's current understanding.

> [!WARNING]
> Instances may be unavailable when loading. Make sure instances exist before accessing. Failure to do so may result in runtime errors.