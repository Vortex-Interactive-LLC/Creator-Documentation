---
title: Mouse & Camera
description: Read the mouse position, what it points at, and the camera in a LocalScript.
---
The mouse and the camera exist on the player's own machine, so these APIs are only available in a `LocalScript`.

## The mouse

```luau
-- LocalScript
local Players = game:GetService("Players")

local mouse = Players.LocalPlayer:GetMouse()
```

`GetMouse` only works on the `LocalPlayer` from a `LocalScript`. Calling it anywhere else raises an error.

| Member | Value |
| --- | --- |
| `mouse.X`, `mouse.Y` | Cursor position in pixels. |
| `mouse.ViewSizeX`, `mouse.ViewSizeY` | Size of the game view in pixels. |
| `mouse.Hit` | A `CFrame` at the point in the world under the cursor. Use `mouse.Hit.Position` for the position. |
| `mouse.Target` | The part under the cursor, or `nil` if the cursor points at empty space. |
| `mouse.UnitRay` | A ray from the camera through the cursor. |
| `mouse.Origin` | A `CFrame` at the start of that ray. |
| `mouse.TargetFilter` | An instance that `Hit` and `Target` look through. Writable. |

```luau
mouse.Button1Down:Connect(function()
    local target = mouse.Target
    if target then
        print("clicked on", target.Name, "at", mouse.Hit.Position)
    end
end)
```

The mouse also has `Button1Up`, `Button2Down`, `Button2Up`, and `Move` signals. Only `TargetFilter` and `Icon` can be set. Writing to any other member raises an error.

To stop the cursor hitting your own character, or something you are dragging, set `TargetFilter`:

```luau
mouse.TargetFilter = Players.LocalPlayer.Character
```

For plain cursor coordinates without a world lookup, `UserInputService:GetMouseLocation()` returns a `Vector2`. See [User Input](user-input.md).

## The camera

```luau
local camera = workspace.CurrentCamera
print(camera.CFrame.Position)
print(camera.ViewportSize)
```

`CurrentCamera` is a [`Camera`](../reference/classes/camera.md) with a `CFrame` and a `ViewportSize`. It is a snapshot taken when you read it, so read `workspace.CurrentCamera` again each frame if you need the camera's current position.

`camera:ScreenPointToRay(x, y, depth)` (also `ViewportPointToRay`) turns a screen position into a ray in the world. The ray's `Origin` is the camera position moved forward by `depth`, which defaults to `0`, and its `Direction` is a unit vector. Combine it with `workspace:Raycast` to find what a screen point hits:

```luau
local ray = workspace.CurrentCamera:ScreenPointToRay(mouse.X, mouse.Y)
local result = workspace:Raycast(ray.Origin, ray.Direction * 500)
if result then
    print("hit", result.Instance.Name)
end
```

> [!NOTE]
> Scripts can read the camera but cannot move it yet. Changing the values on the camera table has no effect on the view.
