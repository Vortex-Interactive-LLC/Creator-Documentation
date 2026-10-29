---
title: UserInputService
description: A service for receiving player input in LocalScripts.
---

`UserInputService` receives keyboard input and other player input on the client. Access it through `game:GetService("UserInputService")` in a `LocalScript`.

## Summary

<details>
<summary><b>Events</b></summary>
<br>

- [InputBegan](#inputbegan): [`Signal`](../datatypes/signal.md)
- [InputEnded](#inputended): [`Signal`](../datatypes/signal.md)

</details>

## Events

### InputBegan

> [`Signal`](../datatypes/signal.md)
>
> `UserInputService.InputBegan`

Fires when input begins. The callback receives an [`InputObject`](../datatypes/input-object.md); its `KeyCode` can be compared with an `Enum.KeyCode` item.

```luau
local input = game:GetService("UserInputService")

input.InputBegan:Connect(function(inputObject)
    if inputObject.KeyCode == Enum.KeyCode.E then
        print("E was pressed")
    end
end)
```

### InputEnded

> [`Signal`](../datatypes/signal.md)
>
> `UserInputService.InputEnded`

An exposed signal that fires when input ends.

## Notes

The service is only available in a `LocalScript`; `game:GetService("UserInputService")` raises an error in a server `Script`.

`InputBegan` and `InputEnded` deliver keyboard keys and mouse buttons, and support `Connect`, `Once`, and `Wait`. Mouse button inputs use `Enum.KeyCode.Unknown`. `InputChanged` fires for mouse movement.

`IsKeyDown` returns `true` for a keyboard key that is currently held, and `false` for mouse buttons. `GetMouseLocation()` returns the cursor position as a `Vector2`.

`KeyboardEnabled` and `MouseEnabled` are `true`, and `GamepadEnabled` and `TouchEnabled` are `false`. `MouseBehavior` and `MouseIconEnabled` read as `nil`.
