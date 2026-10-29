---
title: Instances
description: Learn about Instances in Vortex Studio.
---
> [!Summary]
> Instances are the core objects that make up the game world and its systems. Each instance has a class, properties, and methods, and you can use them to create, organize, and manipulate gameplay objects.

<!--
Written by ElectroTato on the 30th of August, 2026
-->

# Summary

`Instances` are the basic building blocks of objects in a game. Each concrete class has its own [`Properties`](./properties.md) and methods.

You can create a new `Instance` using the [`Instance.new`](../reference/globals/instance-new.md) method in a script by passing the `Instance`'s `ClassName` as the first argument.

Vortex does not currently expose one universal base API on every engine-backed value. For example, `Part` exposes common hierarchy methods while `Player` and `Humanoid` do not. Check the concrete class reference before using a method. The [Instance reference](../reference/classes/instance.md) contains the availability matrix tested in Vortex Studio 0.3.4
