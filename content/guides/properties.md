---
title: Properties
description: Read and write instance properties safely in Vortex.
---
> [!Summary]
> Properties are values stored on an Instance, and you read or write them with dot syntax. Some properties are always available, while others may be optional or restricted by runtime rules.

## Reading and writing

Properties are read with dot syntax and written with assignment. The available properties depend on the instance class and, for character state, on runtime authority rules.
```lua
local part = Instance.new("Part")
part.Transparency = 0.5
print(part.Transparency) -- 0.5
part:Destroy()
```

Temporary Parts in Vortex Studio 0.3.4 have writable appearance, transform, collision, anchoring, and name properties. A live character's Humanoid health and the root part's transform state are not writable, even from a server Script.

## Checking optional properties

Vortex commonly returns `nil` for an unsupported property rather than raising an error on the read. Use `pcall` when a property may be inaccessible or when distinguishing between an unavailable member and a failed read matters.

```lua
local ok, value = pcall(function()
    return object.SomeOptionalProperty
end)

if ok and value ~= nil then
    print(value)
end
```

## Change signals

`Changed`, `GetPropertyChangedSignal`, and attribute-change signals can be present and connectable without firing after a property write. Poll the property when correct behavior depends on observing a change. See [Signals](/content/reference/datatypes/signal.md) and [Attributes](/content/guides/attributes.md).
