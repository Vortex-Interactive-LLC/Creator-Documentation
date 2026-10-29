---
title: Instance.new
description: Creates a new Instance of the given class
---

<!-- 
Instance.new
Revision 1

Written by Arbuzyonak on August 30th, 2026
-->

## Summary

<details>
<summary><b>Constructors</b></summary>

- [new](#new): [`Instance`](../classes/instance.md)

</details>

## Constructors

### new()

> [`Instance`](../classes/instance.md)
>
> `Instance.new(className: string, parent: Instance?)`
>
> Creates a new `Instance` of the class supplied by `className`.

#### Parameters

- `className`: `string` — the class to create.
- `parent`: `Instance?` — optional initial parent for the new instance.

<br/>

## Overview

`Instance.new` creates a new [`Instance`](../classes/instance.md) of the class passed as `className`. It accepts an optional second `parent` argument.

```lua
local part = Instance.new("Part")
print(part)            --> Part
print(part.ClassName)  --> Part
print(part.Name)       --> Part
```

## Parenting

A new instance begins unparented unless you supply a parent. Configure it before assigning its [`Parent`](../classes/instance.md).

Set the parent **last**, after configuring the instance, so scripts listening for new objects receive it fully configured:

```lua
local part = Instance.new("Part")
part.Name = "Platform"
part.Size = Vector3.new(8, 1, 8)
part.Position = Vector3.new(0, 10, 0)
part.Anchored = true
part.Parent = workspace
```

Instance.new() also accepts the parent as an optional second argument:

```lua
local part = Instance.new("Part", Workspace)
part.Name = "Platform"
part.Size = Vector3.new(8, 1, 8)
part.Position = Vector3.new(0, 10, 0)
part.Anchored = true
```

> In Vortex Studio 0.3.4, assigning `Parent` or passing this second argument is accepted, but script-created children are not reliably listed by a service's `GetChildren` or `FindFirstChild`. Do not rely on it to add runtime objects to the editor-authored Workspace hierarchy.

## Default state

> In Vortex Studio 0.3.4, a freshly created `Part` is **anchored**, collidable, and casts shadows. It has the name `Part`, position and rotation `(0, 0, 0)`, an identity `CFrame`, size `(4, 1, 2)`, transparency `0`, and an approximately `(0.64, 0.64, 0.64)` color. Any property you do not set yourself holds the runtime default.

## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later releases.

- `Instance.fromExisting` is not exposed (`nil`) in either Script or LocalScript in 0.3.4.
- Common creatable classes include [`Part`](../classes/part.md), [`Model`](../classes/model.md), [`Folder`](../classes/folder.md), [`Script`](../classes/script.md), [`LocalScript`](../classes/localscript.md), [`ModuleScript`](../classes/modulescript.md), [`IntValue`](../classes/int-value.md), [`StringValue`](../classes/string-value.md), [`BindableEvent`](../classes/bindable-event.md), [`RemoteEvent`](../classes/remote-event.md), [`RemoteFunction`](../classes/remote-function.md), [`PointLight`](../classes/point-light.md), and [`SpotLight`](../classes/spot-light.md). `SpawnLocation`, `Texture`, `Decal`, and `SurfaceAppearance` are not constructible in the tested runtime.

<br/>
