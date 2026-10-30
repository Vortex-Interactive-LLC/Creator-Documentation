---
title: TextButton
description: A clickable GUI object that displays text.
---

## Summary

A `TextButton` is a [`TextLabel`](./text-label.md) that receives input. It is the usual way to make a clickable button.

### Example

```luau
local button = Instance.new("TextButton")
button.Text = "Play"
button.Parent = screenGui

button.MouseButton1Click:Connect(function()
    print("clicked")
end)
```

## Properties

- `Text` - `string`, up to 2000 characters. Defaults to `"Button"`;
- `TextColor3` - [`Color3`](../datatypes/color3.md), defaults to `0.11, 0.11, 0.11`;
- `TextSize` - `number`, defaults to `14`;
- `TextTransparency` - `number`, defaults to `0`;
- `TextScaled` - `boolean`, defaults to `false`;
- `TextWrapped` - `boolean`, defaults to `false`;
- `TextXAlignment` - `Enum.TextXAlignment`, defaults to `Center`;
- `TextYAlignment` - `Enum.TextYAlignment`, defaults to `Center`;
- `Font` - `Enum.Font`, defaults to `Figtree`;
- `AutoButtonColor` - `boolean`, defaults to `true`;
- every property of a [`Frame`](./frame.md), with a default `Size` of `0, 200, 0, 50`, a default `BackgroundColor3` of `0.64, 0.64, 0.65`, and `Active` set to `true`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
