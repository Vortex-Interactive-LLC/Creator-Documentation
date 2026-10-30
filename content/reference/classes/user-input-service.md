---
title: UserInputService
description: A service for receiving keyboard and mouse input in LocalScripts.
---

## Summary

`UserInputService` reports keyboard and mouse input on the player's machine. Access it with `game:GetService("UserInputService")` in a `LocalScript`; it raises an error in a server `Script`. See the [User Input guide](../../guides/user-input.md).

## Properties

- `KeyboardEnabled` - `boolean`, `true`;
- `MouseEnabled` - `boolean`, `true`;
- `TouchEnabled` - `boolean`, `false`;
- `GamepadEnabled` - `boolean`, `false`.

`MouseBehavior` and `MouseIconEnabled` read as `nil`.

## Methods

### IsKeyDown

> `UserInputService:IsKeyDown(keyCode: Enum.KeyCode): boolean`

Returns whether a keyboard key is currently held down. It returns `false` for mouse buttons.

```luau
local UserInputService = game:GetService("UserInputService")

if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
    print("Left Shift is held")
end
```

### GetMouseLocation

> `UserInputService:GetMouseLocation(): Vector2`

Returns the cursor position in pixels as a [`Vector2`](../datatypes/vector2.md).

## Events

All events support `Connect`, `Once`, and `Wait`, and deliver both processed and unprocessed input.

### InputBegan

> `UserInputService.InputBegan(input: InputObject, gameProcessedEvent: boolean)`

Fires when a key or mouse button is pressed. `input` is an [`InputObject`](../datatypes/input-object.md). `gameProcessedEvent` is `true` when the game already handled the input, for example a click on a GUI button. Mouse buttons use `Enum.KeyCode.Unknown` and carry the cursor position.

```luau
UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if gameProcessedEvent then return end

    if input.KeyCode == Enum.KeyCode.R then
        print("R pressed")
    end
end)
```

### InputEnded

> `UserInputService.InputEnded(input: InputObject, gameProcessedEvent: boolean)`

Fires when a key or mouse button is released.

### InputChanged

> `UserInputService.InputChanged(input: InputObject, gameProcessedEvent: boolean)`

Fires when the mouse moves. `input.Delta` is how far the cursor moved.
