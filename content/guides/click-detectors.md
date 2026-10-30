---
title: ClickDetectors
description: Make a part or model clickable with a ClickDetector.
---
A [`ClickDetector`](../reference/classes/click-detector.md) makes its parent clickable. Put one inside a `Part` or a `Model`, and clicking any part of it fires the detector's events.

```luau
-- Script
local detector = workspace.Door.ClickDetector

detector.MouseClick:Connect(function(player)
    print(player.Name, "clicked the door")
end)
```

Every event passes the `Player` who caused it. You can connect from a server `Script`, which is the usual place for gameplay, or from a `LocalScript`.

## Events

- `MouseClick` fires when the player presses and releases the left mouse button on the parent.
- `RightMouseClick` does the same for the right button.
- `MouseHoverEnter` fires when the cursor moves onto the parent.
- `MouseHoverLeave` fires when it moves off.

A click needs the press and the release to happen on the same detector. Pressing on the part and releasing somewhere else does not fire `MouseClick`.

## Reach

`MaxActivationDistance` is how far the player's character can be from the point they clicked. It defaults to 32 studs. A click on a part farther away than that does nothing.

```luau
detector.MaxActivationDistance = 10
```

The server checks the distance again with a small margin for lag, so a click from far outside the range is ignored even if the client sent it.

## Creating one from a script

```luau
local part = Instance.new("Part")
part.Anchored = true
part.Parent = workspace

local detector = Instance.new("ClickDetector")
detector.Parent = part
detector.MouseClick:Connect(function(player)
    part.Color = Color3.fromRGB(255, 0, 0)
end)
```

> [!NOTE]
> Clicks on GUI buttons and other interface elements do not reach a `ClickDetector`. The cursor changes to a pointing hand while it is over a clickable part.
