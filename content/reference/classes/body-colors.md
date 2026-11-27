---
title: BodyColors
description: The colours of a character's body parts.
---

## Summary

A `BodyColors` in a character sets the colour of each body part of the avatar. A character is given one when it spawns or when a [`HumanoidDescription`](./humanoid-description.md) is applied.

```luau
local colors = character:FindFirstChildOfClass("BodyColors")
colors.TorsoColor3 = Color3.fromRGB(255, 0, 0)
```

## Properties

- `HeadColor3`, `LeftArmColor3`, `RightArmColor3`, `TorsoColor3`, `LeftLegColor3`, `RightLegColor3` - [`Color3`](../datatypes/color3.md), the colour of each body part. `HeadColor3`, `LeftArmColor3`, and `RightArmColor3` default to white, `TorsoColor3` to purple, and the leg colours to dark blue;
- `Name`, `ClassName`, `Parent`.
