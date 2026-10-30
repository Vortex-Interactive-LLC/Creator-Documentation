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

Parts have writable appearance, transform, collision, anchoring, and name properties. A live character is more restricted: the root part's `Size` and `Orientation` are read-only, and some character state is server-authoritative, so client writes to it are rejected.

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

`Changed`, `GetPropertyChangedSignal`, and `GetAttributeChangedSignal` fire when a property or attribute changes on an instance that is parented into the game. Instances with no parent do not fire them, and a change made in the same frame as the instance was parented is missed, so wait a frame after setting `Parent` before relying on them. See [Signals](../reference/datatypes/signal.md) and [Attributes](./attributes.md).
