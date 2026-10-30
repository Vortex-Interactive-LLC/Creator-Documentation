---
title: TextLabel
description: A GUI object that displays text.
---

## Summary

A `TextLabel` is a box with text in it. It has every property of a [`Frame`](./frame.md) as well.

### Example

```luau
local label = Instance.new("TextLabel")
label.Text = "Score: 0"
label.TextSize = 24
label.Parent = screenGui
```

## Properties

- `Text` - `string`, up to 2000 characters. Defaults to `"Label"`;
- `TextColor3` - [`Color3`](../datatypes/color3.md), defaults to `0.11, 0.11, 0.11`;
- `TextSize` - `number`, defaults to `14`;
- `TextTransparency` - `number`, defaults to `0`;
- `TextScaled` - `boolean`, defaults to `false`;
- `TextWrapped` - `boolean`, defaults to `false`;
- `TextXAlignment` - `Enum.TextXAlignment`, defaults to `Center`;
- `TextYAlignment` - `Enum.TextYAlignment`, defaults to `Center`;
- `Font` - `Enum.Font`, defaults to `Figtree`;
- every property of a [`Frame`](./frame.md), with a default `Size` of `0, 200, 0, 50`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, and `Activated`. Only objects that receive input fire them: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
