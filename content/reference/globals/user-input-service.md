---
title: UserInputService
description: User Input Service is used to detect a players device, and also used to detect inputs from the Player.
---

## Methods

### IsKeyDown

Returns whether a certain key is being held down.

```
UserInputService:IsKeyDown(KeyCode: Enum.KeyCode): Boolean
```

#### Parameters

```
KeyCode: Enum.KeyCode
The Enum.KeyCode of the key
```

#### Returns

```
Boolean
Whether the specified key is being held down or not.
```

This method returns true if the specified key is held down, otherwise it returns false.

#### Examples

```luau
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function()
    if UserInputService:IsKeyDown(Enum.KeyCode.LeftShift) then
        print("Left Shift")
    end
end)
```

## Events

### InputBegan

Fires whenever the Player interacts with an input device.

```
UserInputService.InputBegan(Input: InputObject, GameProcessedEvent: Boolean)
```

#### Parameters

```
Input: Input Object
An Input object which contains information about the user's input.
```

```
GameProcessedEvent: Boolean
Whether the Engine observed an action and acted on it. If a button was touched or clicked from this input, GameProcessedEvent will be true.
```

#### Examples

```luau
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function(Input, GameProcessedEvent)
    if GameProcessedEvent then
        print("Game Processed Event")
    end

    if Input.KeyCode == Enum.KeyCode.R then
        print("R")
    end
end)
```

### InputEnded

Fires whenever the Player stops interacting with an input device.

```
UserInputService.InputEnded(Input: InputObject, GameProcessedEvent: Boolean)
```

#### Parameters

```
Input: Input Object
An Input object which contains information about the user's input.
```

```
GameProcessedEvent: Boolean
Whether the Engine observed an action and acted on it. If a button was touched or clicked from this input, GameProcessedEvent will be true.
```

#### Examples

```luau
local UserInputService = game:GetService("UserInputService")

UserInputService.InputEnded:Connect(function(Input, GameProcessedEvent)
    if GameProcessedEvent then
        print("Game Processed Event")
    end

    print("Input Ended.")
end)
```

## Vortex Studio 0.3.4 notes

The service is available in a `LocalScript` and absent in a normal server `Script`. `InputBegan:Once` and `InputBegan:Wait` both delivered a right-mouse button input in a LocalScript. Ordinary `InputBegan:Connect` delivered keyboard keys (`S`, `A`, `W`, and `Space`) and mouse buttons; mouse buttons use `Enum.KeyCode.Unknown`. Both processed and unprocessed input were observed.

`IsKeyDown` is available. It returned `true` for the keyboard key currently being pressed and `false` for mouse-button events.

The tested 0.3.4 client reported `KeyboardEnabled=true`, `MouseEnabled=true`, `GamepadEnabled=false`, and `TouchEnabled=false`.

`InputEnded` is connectable in a LocalScript and delivered both keyboard and mouse-button releases. `InputChanged` reads as `nil` and cannot be connected. `GetMouseLocation` is unavailable, while `MouseBehavior` and `MouseIconEnabled` read as `nil`. These results were revalidated in 0.3.4.
