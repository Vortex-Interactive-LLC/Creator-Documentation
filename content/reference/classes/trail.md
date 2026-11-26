---
title: Trail
description: A ribbon left behind a moving pair of attachments.
---

## Summary

A `Trail` leaves a fading ribbon behind two [`Attachment`](./attachment.md)s as they move, such as the tip and base of a sword.

```luau
local trail = Instance.new("Trail")
trail.Attachment0 = sword.Tip
trail.Attachment1 = sword.Base
trail.Lifetime = 0.4
trail.Color = ColorSequence.new(Color3.new(1, 1, 1), Color3.new(0.4, 0.7, 1))
trail.LightEmission = 1
trail.Parent = sword
```

## Properties

- `Attachment0`, `Attachment1` - the two edges of the ribbon;
- `Enabled` - `boolean`, whether new ribbon is added. Defaults to `true`;
- `Color` - [`ColorSequence`](../datatypes/color-sequence.md), color from newest to oldest. Defaults to white;
- `Transparency` - [`NumberSequence`](../datatypes/number-sequence.md), transparency from newest to oldest. Defaults to `0` fading to `1`;
- `WidthScale` - [`NumberSequence`](../datatypes/number-sequence.md), scales the width from newest to oldest. Defaults to `1`;
- `Lifetime` - `number`, seconds before a piece fades away. Defaults to `2`;
- `MinLength` - `number`, how far the attachments move before a new piece is added. Defaults to `0.1`;
- `MaxLength` - `number`, caps the length of the trail. `0` means no cap. Defaults to `0`;
- `FaceCamera`, `LightEmission`, `Texture`, `TextureLength`, `TextureMode` - work as they do on [`Beam`](./beam.md);
- `Name`, `ClassName`, `Parent`.

## Methods

- `Clear()` - removes the whole trail at once.

## Notes

- Trails are drawn on the client, so the shape comes from what each player sees. It is not saved or sent over the network.
