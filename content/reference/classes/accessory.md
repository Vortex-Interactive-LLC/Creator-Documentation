---
title: Accessory
description: An item such as a hat or hair worn by a character.
---

## Summary

An `Accessory` in a character makes the avatar wear one accessory. `AssetId` is the catalogue id of the accessory model. Add it with [`Humanoid:AddAccessory`](./humanoid.md#addaccessory), list the worn ones with [`Humanoid:GetAccessories`](./humanoid.md#getaccessories), and remove them with [`Humanoid:RemoveAccessories`](./humanoid.md#removeaccessories).

```luau
local accessory = Instance.new("Accessory")
accessory.AccessoryType = Enum.AccessoryType.Hat
accessory.AssetId = 366
humanoid:AddAccessory(accessory)
```

## Properties

- `AccessoryType` - `Enum.AccessoryType`, defaults to `Hat`. Where the accessory is worn: `Hat`, `Hair`, `Face`, `Neck`, `Shoulder`, `Front`, `Back`, or `Waist`. `Unknown` is not drawn;
- `AssetId` - the asset id of the accessory model. Defaults to none, which is not drawn;
- `Name`, `ClassName`, `Parent`.

There is no `Handle` part. The accessory is drawn from its model and follows the avatar's body.
