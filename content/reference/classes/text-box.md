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
- `CursorPosition` - `number`, the position of the cursor in `Text`, counting from `1` for the position before the first character. `-1` when the box does not have focus;
- `SelectionStart` - `number`, the position where the selection started, or `-1` when no text is selected;
- every text property of a [`TextLabel`](./text-label.md), such as `TextColor3`, `TextSize`, `TextXAlignment` and `Font`;
- `TextStrokeColor3`, `TextStrokeTransparency` and `TextTruncate`, as on a [`TextLabel`](./text-label.md);
- `TextBounds` - [`Vector2`](../datatypes/vector2.md), read-only, as on a [`TextLabel`](./text-label.md);
- every property of a [`Frame`](./frame.md), with a default `Size` of `0, 200, 0, 50`.

## Signals

- `Focused` - fires when the player clicks into the box;
- `FocusLost(enterPressed)` - fires when the box loses focus. `enterPressed` is `true` only when a single-line box was ended with Enter. Clicking elsewhere or pressing Escape gives `false`;
- plus the mouse signals listed in the [Building GUIs guide](../../guides/gui.md#responding-to-input).

## Methods

- `CaptureFocus()` - puts the cursor in the box as if the player had clicked it, including clearing `Text` when `ClearTextOnFocus` is `true`. `Focused` fires. Does nothing if the box cannot be focused (hidden, not editable, in the world, or rotated). Any other box that had focus loses it first;
- `ReleaseFocus(submitted)` - takes focus away. `submitted` is optional and defaults to `false`; it is the `enterPressed` value that `FocusLost` receives. Does nothing if the box does not have focus;
- `IsFocused()` - returns `true` while this box has focus. It reflects the state as of the last frame, so right after `CaptureFocus()` it can still be `false`.

## Notes

- While a box has focus, typing does not move the character or trigger keybinds, and `UserInputService` does not report the keys.
- `Text` changes reach scripts about a frame after the player types.
- A `TextBox` inside a `BillboardGui` or `SurfaceGui` cannot be focused.
- A box that is rotated, or inside a rotated object, cannot be focused, by the player or by `CaptureFocus`.
