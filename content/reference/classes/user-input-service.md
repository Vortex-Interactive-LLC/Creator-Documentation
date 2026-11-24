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
- `GamepadEnabled` - `boolean`, `false`;
- `MouseBehavior` - `Enum.MouseBehavior`, defaults to `Default`. `LockCenter` hides the cursor and keeps it in the middle of the window, and `LockCurrentPosition` keeps it where it is. While it is not `Default`, [`GetMouseDelta`](#getmousedelta) reports how far the mouse moved;
- `MouseIconEnabled` - `boolean`, defaults to `true`. When `false`, the cursor is not drawn.

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

### GetMouseDelta

> `UserInputService:GetMouseDelta(): Vector2`

Returns how far the mouse moved since the last frame, in pixels, as a [`Vector2`](../datatypes/vector2.md). It returns `0, 0` while `MouseBehavior` is `Default`, and while a [`Modal`](./text-button.md) button is on screen.

```luau
UserInputService.MouseBehavior = Enum.MouseBehavior.LockCenter

game:GetService("RunService").RenderStepped:Connect(function()
    local delta = UserInputService:GetMouseDelta()
    print(delta.X, delta.Y)
end)
```

### SetClipboardText

> `UserInputService:SetClipboardText(text: string): boolean`

Copies `text` to the player's clipboard and returns `true`. It returns `false` when the window is not focused, when `text` is longer than 256 KB, or when it was called less than half a second after the last copy.

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

### TextBoxFocused

> `UserInputService.TextBoxFocused(textBox: TextBox)`

Fires when the player clicks into a [`TextBox`](./text-box.md), or when `CaptureFocus` is called on one. The box is passed to the handler.

### TextBoxFocusReleased

> `UserInputService.TextBoxFocusReleased(textBox: TextBox)`

Fires when a [`TextBox`](./text-box.md) loses focus. The box is passed to the handler.

### ClipboardPasted

> `UserInputService.ClipboardPasted(text: string)`

Fires when the player pastes text into a [`TextBox`](./text-box.md). The pasted text is passed to the handler.

### WindowFocused

> `UserInputService.WindowFocused()`

Fires when the game window gains focus.

### WindowFocusReleased

> `UserInputService.WindowFocusReleased()`

Fires when the game window loses focus.
