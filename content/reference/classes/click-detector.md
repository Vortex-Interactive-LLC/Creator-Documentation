---
title: ClickDetector
description: Makes its parent Part or Model respond to mouse clicks.
---

## Summary

A `ClickDetector` placed inside a `Part` or `Model` makes that object clickable. See the [ClickDetectors guide](../../guides/click-detectors.md).

### Example

```luau
local detector = Instance.new("ClickDetector")
detector.MaxActivationDistance = 16
detector.Parent = workspace.Door

detector.MouseClick:Connect(function(player)
    print(player.Name, "clicked")
end)
```

## Properties

- `MaxActivationDistance` - `number`, how far in studs the clicking player's character can be from the clicked point. Defaults to `32`. Negative values are treated as `0`;
- `Name` - the name of the instance;
- `ClassName` - `"ClickDetector"`;
- `Parent` - the `Part` or `Model` it makes clickable.

## Signals

All four signals pass the [`Player`](./player.md) who triggered them and support `Connect`, `Once`, and `Wait`.

- `MouseClick` - the left button was pressed and released on the parent;
- `RightMouseClick` - the right button was pressed and released on the parent;
- `MouseHoverEnter` - the cursor moved onto the parent;
- `MouseHoverLeave` - the cursor moved off the parent.
