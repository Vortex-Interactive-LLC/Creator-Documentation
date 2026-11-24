---
title: HumanoidDescription
description: Describes the look of a character, to apply to a Humanoid.
---

## Summary

A `HumanoidDescription` holds the colours, clothing, face, body type, and accessories of an avatar. Apply it to a character with [`Humanoid:ApplyDescription`](./humanoid.md#applydescription), or read the look of a character with [`Humanoid:GetAppliedDescription`](./humanoid.md#getapplieddescription).

```luau
local description = Instance.new("HumanoidDescription")
description.HeadColor = Color3.fromRGB(255, 204, 153)
description.HatAccessory = "1234567"
description.Shirt = 7654321

humanoid:ApplyDescription(description)
```

## Properties

- `HeadColor`, `TorsoColor`, `LeftArmColor`, `RightArmColor`, `LeftLegColor`, `RightLegColor` - [`Color3`](../datatypes/color3.md), the colour of each body part. `HeadColor`, `LeftArmColor`, and `RightArmColor` default to white, `TorsoColor` to purple, and the leg colours to dark blue;
- `Face`, `Shirt`, `Pants` - `number`, the asset id of the face, shirt, and pants. Whole numbers only. Defaults to `0`, which uses none;
- `BodyType` - `Enum.BodyType`: `Male` or `Female`. Defaults to `Male`;
- `HatAccessory`, `HairAccessory`, `FaceAccessory`, `NeckAccessory`, `ShouldersAccessory`, `FrontAccessory`, `BackAccessory`, `WaistAccessory` - `string`, the asset ids of the accessories worn in that slot, separated by commas, such as `"1234567,7654321"`. Empty by default. An id that is not a whole number above `0` raises an error;
- `Name`, `ClassName`, `Parent`.

An accessory id cannot be used in more than one property, and applying a description that does this raises an error.
