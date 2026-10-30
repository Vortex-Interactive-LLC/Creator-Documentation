---
title: ForceField
description: Protects a character from damage dealt with TakeDamage.
---

## Summary

While a `ForceField` is a child of a character, [`Humanoid:TakeDamage`](./humanoid.md) does nothing. A newly spawned character has one for a few seconds.

```lua
local forceField = Instance.new("ForceField")
forceField.Parent = character

task.wait(5)
forceField:Destroy()
```

## Properties

- `Name`, `ClassName`, `Parent`.

Setting `Health` directly is not blocked by a `ForceField`.
