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
- `RichText` - `boolean`, reads `Text` as markup, see below. Defaults to `false`;
- `TextStrokeColor3` - [`Color3`](../datatypes/color3.md), the colour of a 1 pixel outline around the text. Defaults to `0, 0, 0`. For a thicker outline use a [`UIStroke`](./ui-stroke.md);
- `TextStrokeTransparency` - `number`, defaults to `1`, which draws no outline;
- `TextTruncate` - `Enum.TextTruncate`: `AtEnd` cuts text that does not fit and ends it with an ellipsis, wrapped text is cut after the last row that fits. Defaults to `None`;
- `TextBounds` - [`Vector2`](../datatypes/vector2.md), read-only. The size in pixels of the text as drawn, which is `0, 0` for empty or `TextScaled` text and for a moment after the game starts, before fonts are ready;
- `TextXAlignment` - `Enum.TextXAlignment`, defaults to `Center`;
- `TextYAlignment` - `Enum.TextYAlignment`, defaults to `Center`;
- `Font` - `Enum.Font`, defaults to `Figtree`;
- `AutoButtonColor` - `boolean`, defaults to `true`;
- every property of a [`Frame`](./frame.md), with a default `Size` of `0, 200, 0, 50`, a default `BackgroundColor3` of `0.64, 0.64, 0.65`, and `Active` set to `true`.

## Rich text

Set `RichText` to `true` to style parts of `Text` with tags:

| Tag | Effect |
|---|---|
| `<b>...</b>` | bold. Drawn by overlaying the text with a slight offset, since the fonts have no bold weight |
| `<i>...</i>` | italic |
| `<u>...</u>` | underline |
| `<s>...</s>` | strikethrough |
| `<font color="#FFD54A">...</font>` | colour, as `#RGB`, `#RRGGBB` or `rgb(255, 213, 74)` |
| `<font size="30">...</font>` | size in pixels |
| `<br/>` | line break |

```luau
label.RichText = true
label.Text = 'Cost <font color="#FFD54A"><b>2,400</b></font> coins'
```

Tags can be nested. `&lt;`, `&gt;`, `&amp;`, `&quot;` and `&apos;` write the characters themselves, and a `<` that does not start a known tag is shown as it is. A closing tag also closes any tag opened inside it. The text outline from `UIStroke`, `TextBounds` and `AutomaticSize` follow `<font size>` and `<i>`. Bold is only drawn as an overlay, so it does not widen the text or its outline. `RichText` does nothing on a `TextBox`.

## Signals

`MouseButton1Click`, `MouseButton2Click`, `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up`, `MouseEnter`, `MouseLeave`, `Activated`, and the pointer signals `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`. The pointer signals fire for every visible object under the pointer. The others only fire for objects that receive input: buttons and objects with `Active` set to `true`. See the signal table in the [Building GUIs guide](../../guides/gui.md#responding-to-input).
