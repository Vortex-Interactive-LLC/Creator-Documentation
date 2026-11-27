---
title: Pants
description: The pants worn by a character.
---

## Summary

A `Pants` in a character sets the pants of the avatar. A character without a `Pants` wears none. A character is given one when it spawns or when a [`HumanoidDescription`](./humanoid-description.md) is applied.

```luau
local pants = character:FindFirstChildOfClass("Pants")
pants.PantsTemplate = 857
```

## Properties

- `PantsTemplate` - the asset id of the pants. Defaults to none;
- `Name`, `ClassName`, `Parent`.
