---
title: TextBox
description: A GUI object the player can type into.
---

## Summary

A `TextBox` is a [`TextLabel`](./text-label.md) the player can click and type into. Use it for codes, search fields and names.

### Example

```luau
local box = Instance.new("TextBox")
box.PlaceholderText = "Enter a code"
box.Text = ""
box.Parent = screenGui

box.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        print("submitted", box.Text)
    end
end)
```

## Properties

- `Text` - `string`, up to 2000 characters. Defaults to `"TextBox"`. It updates as the player types;
- `PlaceholderText` - `string`, shown in `PlaceholderColor3` while `Text` is empty. Defaults to empty;
- `PlaceholderColor3` - [`Color3`](../datatypes/color3.md), defaults to `0.7, 0.7, 0.7`;
- `ClearTextOnFocus` - `boolean`, defaults to `true`. Clears `Text` when the player clicks into the box;
- `MultiLine` - `boolean`, defaults to `false`. When `true`, Enter adds a new line instead of ending the edit;
- `TextEditable` - `boolean`, defaults to `true`. When `false` the box cannot be focused;
- every text property of a [`TextLabel`](./text-label.md), such as `TextColor3`, `TextSize`, `TextXAlignment` and `Font`;
- every property of a [`Frame`](./frame.md), with a default `Size` of `0, 200, 0, 50`.

## Signals

- `Focused` - fires when the player clicks into the box;
- `FocusLost(enterPressed)` - fires when the box loses focus. `enterPressed` is `true` only when a single-line box was ended with Enter. Clicking elsewhere or pressing Escape gives `false`;
- plus the mouse signals listed in the [Building GUIs guide](../../guides/gui.md#responding-to-input).

## Notes

- While a box has focus, typing does not move the character or trigger keybinds, and `UserInputService` does not report the keys.
- `Text` changes reach scripts about a frame after the player types.
- A `TextBox` inside a `BillboardGui` or `SurfaceGui` cannot be focused.
- `CaptureFocus`, `ReleaseFocus` and `IsFocused` are not available yet.
