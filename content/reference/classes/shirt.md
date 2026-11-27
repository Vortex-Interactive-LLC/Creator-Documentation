---
title: Shirt
description: The shirt worn by a character.
---

## Summary

A `Shirt` in a character sets the shirt of the avatar. A character without a `Shirt` wears none. A character is given one when it spawns or when a [`HumanoidDescription`](./humanoid-description.md) is applied.

```luau
local shirt = character:FindFirstChildOfClass("Shirt")
shirt.ShirtTemplate = 1100
```

## Properties

- `ShirtTemplate` - the asset id of the shirt. Defaults to none;
- `Name`, `ClassName`, `Parent`.
