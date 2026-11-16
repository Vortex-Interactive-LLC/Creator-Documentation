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

`CurrentCamera` is a [`Camera`](../reference/classes/camera.md) with a `CFrame`, a `FieldOfView` and a `ViewportSize`.

`camera:ScreenPointToRay(x, y, depth)` (also `ViewportPointToRay`) turns a screen position into a ray in the world. The ray's `Origin` is the camera position moved forward by `depth`, which defaults to `0`, and its `Direction` is a unit vector. Combine it with `workspace:Raycast` to find what a screen point hits:

```luau
local ray = workspace.CurrentCamera:ScreenPointToRay(mouse.X, mouse.Y)
local result = workspace:Raycast(ray.Origin, ray.Direction * 500)
if result then
    print("hit", result.Instance.Name)
end
```

## Moving the camera

By default the camera follows the player's character. Set `CameraType` to `Scriptable` to move it yourself, then write `CFrame` and `FieldOfView`:

```luau
-- LocalScript
local camera = workspace.CurrentCamera

camera.CameraType = Enum.CameraType.Scriptable
camera.CFrame = CFrame.lookAt(Vector3.new(0, 60, 80), Vector3.new(0, 0, 0))
camera.FieldOfView = 50
```

Switching to `Scriptable` keeps the camera where it was until you set `CFrame`. Set `CameraType` back to `Custom` to return to the default camera.

While `CameraType` is `Scriptable`, the default mouse look and zoom are off, so read the mouse yourself if you want them. Movement keys still move the character relative to where the camera faces.

## Camera limits

[`StarterPlayer`](../reference/classes/starter-player.md) sets how far the camera can zoom, whether the camera is locked to first person, and whether players can use shift lock. Set them in Studio, or from a `LocalScript`:

```luau
-- LocalScript
local starter = game:GetService("StarterPlayer")

starter.CameraMinZoomDistance = 8
starter.CameraMaxZoomDistance = 40
starter.EnableMouseLockOption = false
```

## Turning the camera in steps

This keeps the camera behind the character and turns it 45 degrees with the comma and period keys. Holding the right mouse button and dragging looks around. `R` returns to the default camera.

```luau
-- LocalScript
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local camera = workspace.CurrentCamera
local step = math.rad(45)
local yaw, pitch = 0, 0.35
local active = false
local looking = false

local function activate()
    if active then return end
    local look = camera.CFrame.LookVector
    yaw = math.atan2(-look.X, -look.Z)
    pitch = math.asin(math.clamp(-look.Y, -1, 1))
    active = true
    camera.CameraType = Enum.CameraType.Scriptable
end

RunService.RenderStepped:Connect(function()
    local character = Players.LocalPlayer.Character
    local root = character and character:FindFirstChild("HumanoidRootPart")
    if not active or not root then return end

    camera.CFrame = CFrame.new(root.Position + Vector3.new(0, 4.64, 0))
        * CFrame.Angles(0, yaw, 0)
        * CFrame.Angles(-pitch, 0, 0)
        * CFrame.new(0, 0, 25.6)
end)

UserInputService.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton2 then
        looking = true
    elseif input.KeyCode == Enum.KeyCode.Comma then
        activate()
        yaw = math.floor((yaw + step) / step + 0.5) * step
    elseif input.KeyCode == Enum.KeyCode.Period then
        activate()
        yaw = math.floor((yaw - step) / step + 0.5) * step
    elseif input.KeyCode == Enum.KeyCode.R then
        active = false
        camera.CameraType = Enum.CameraType.Custom
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton2 then
        looking = false
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input.UserInputType ~= Enum.UserInputType.MouseMovement or not active or not looking then return end
    yaw -= input.Delta.X * 0.002 * math.pi
    pitch = math.clamp(pitch + input.Delta.Y * 0.0015 * math.pi, -math.rad(80), math.rad(80))
end)
```

> [!NOTE]
> The period key also opens the emote wheel while it is held. Use `Enum.KeyCode.LeftBracket` and `Enum.KeyCode.RightBracket` to avoid that.
