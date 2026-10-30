---
title: User Input
description: Detect keyboard and mouse input in a LocalScript with UserInputService.
---
`UserInputService` reports what the player presses and does with the keyboard and mouse. It is only available in a `LocalScript`. Calling `game:GetService("UserInputService")` in a server `Script` raises an error, so send input to the server with a [`RemoteEvent`](../reference/classes/remote-event.md).

## Key presses

```luau
-- LocalScript
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end

    if input.KeyCode == Enum.KeyCode.E then
        print("E pressed")
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.E then
        print("E released")
    end
end)
```

`input` is an [`InputObject`](../reference/datatypes/input-object.md). `gameProcessed` is `true` when the game already handled the input, for example when it clicked a GUI button. Check it first so your script does not react to the same click twice.

## Held keys

`IsKeyDown` returns whether a keyboard key is held right now. It returns `false` for mouse buttons.

```luau
if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
    print("sprinting")
end
```

## Mouse

Mouse buttons arrive through `InputBegan` and `InputEnded` with `KeyCode` set to `Enum.KeyCode.Unknown`, and the input's `Position` holds the cursor position. Mouse movement fires `InputChanged`, with `Delta` set to how far the cursor moved. `GetMouseLocation()` returns the current cursor position as a `Vector2`.

```luau
local pos = UserInputService:GetMouseLocation()
print(pos.X, pos.Y)
```

For the 3D position under the cursor, see [Mouse & Camera](mouse-and-camera.md).

## Sending input to the server

A `Vector2` can be sent through a `RemoteEvent`, so you can pass the mouse position straight to the server:

```luau
remoteEvent:FireServer(UserInputService:GetMouseLocation())
```

> [!NOTE]
> The engine currently reports `KeyboardEnabled` and `MouseEnabled` as `true` and `TouchEnabled` and `GamepadEnabled` as `false`. Touch and gamepad input are not delivered.

See the [`UserInputService`](../reference/classes/user-input-service.md) reference.
