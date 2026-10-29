---
title: UserInputService
description: A service for receiving player input in LocalScripts.
---

`UserInputService` receives keyboard input and other player input on the client.
Access it through `game:GetService("UserInputService")` in a `LocalScript`.

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

Fires when input begins. The callback receives an
[`InputObject`](../datatypes/input-object.md); its `KeyCode`
can be compared with an `Enum.KeyCode` item.

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

## Vortex Studio 0.3.4 notes

`InputBegan:Once` and `InputBegan:Wait` both delivered right-mouse-button input
in a LocalScript. A normal server Script has no usable UserInputService.
Ordinary `InputBegan:Connect` also delivered keyboard keys (`S`, `A`, `W`, and
`Space`) and mouse buttons. Keyboard events carried their KeyCode; mouse
buttons used `Enum.KeyCode.Unknown`. 
Both `gameProcessed=false` and `gameProcessed = true were` were observed.

`IsKeyDown` is available: it returned `true` for a keyboard key that was
currently being pressed and `false` for mouse-button events.
The tested 0.3.4 client reported `KeyboardEnabled=true`, `MouseEnabled=true`,
`GamepadEnabled=false`, and `TouchEnabled=false`.

`InputEnded` is connectable in a LocalScript and delivered both keyboard and
mouse-button releases. `InputChanged` reads as `nil` and cannot be connected.
`GetMouseLocation` is unavailable, while `MouseBehavior` and
`MouseIconEnabled` read as `nil`. These results were revalidated in Vortex Studio 0.3.4.
