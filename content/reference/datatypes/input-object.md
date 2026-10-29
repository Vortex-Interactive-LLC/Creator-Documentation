---
title: InputObject
description: Describes one client input delivered by UserInputService.
---

An `InputObject` is a table describing one client input. Scripts do not construct it directly. A client [`LocalScript`](../classes/localscript.md) receives it from [`UserInputService`](../classes/user-input-service.md) signals such as `InputBegan` and `InputEnded`.

The signal callback also receives `gameProcessed`, a Boolean that reports whether the engine already handled the input. Gameplay controls commonly return early when it is `true`, which prevents typing in chat or using an engine control from also triggering the game action.

## Properties

### KeyCode

> [`EnumItem`](./enumitem.md)
>
> The keyboard key associated with the input.

Keyboard input supplies the matching `Enum.KeyCode` item. Mouse buttons use `Enum.KeyCode.Unknown`, so use `UserInputType` to distinguish mouse buttons.

### UserInputType

> [`EnumItem`](./enumitem.md)
>
> The device action that produced the input.

Examples include `Enum.UserInputType.Keyboard`, `MouseButton1`, and `MouseButton2`.

### Position

> [`Vector3`](./vector3.md)
>
> Positional data supplied with the input.

### Delta

> [`Vector3`](./vector3.md)
>
> The change in position supplied with the input.

## Keyboard and mouse example

```luau
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then
        return
    end

    if input.UserInputType == Enum.UserInputType.Keyboard
        and input.KeyCode == Enum.KeyCode.E then
        print("E was pressed")
    elseif input.UserInputType == Enum.UserInputType.MouseButton1 then
        print("The left mouse button was pressed")
    end
end)
```

Compare enum items directly. Do not compare `KeyCode` or `UserInputType` with strings such as `"E"` or `"MouseButton1"`.

## Notes

`Position` and `Delta` are `Vector3` values. For mouse button inputs, `Position` is the cursor position; for keyboard inputs it is `(0, 0, 0)`. For the mouse-movement input delivered by `UserInputService.InputChanged`, `Delta` is how far the mouse moved.

`UserInputState`, `Changed`, and `IsModifierKeyDown` read as `nil`. Touch and gamepad InputObjects are not available.
