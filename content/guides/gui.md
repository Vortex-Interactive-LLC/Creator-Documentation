---
title: Building GUIs
description: Build on-screen and in-world interfaces and respond to clicks.
---
A GUI is a tree of instances. A [`ScreenGui`](../reference/classes/screen-gui.md) is the root, and objects such as [`Frame`](../reference/classes/frame.md), [`TextLabel`](../reference/classes/text-label.md), [`TextButton`](../reference/classes/text-button.md) and [`ImageLabel`](../reference/classes/image-label.md), [`ImageButton`](../reference/classes/image-button.md) go inside it. Anything inside an object is drawn relative to it.

```text
StarterGui
└── ScreenGui
    └── Frame
        ├── UICorner
        ├── UIListLayout
        ├── TextLabel
        └── TextButton
```

GUIs are drawn and handled on the player's own machine, so script them with a `LocalScript`.

## Where GUIs live

Put the `ScreenGui` in [`StarterGui`](../reference/classes/starter-gui.md). When a player joins, they get a [`PlayerGui`](../reference/classes/player-gui.md) containing a copy of everything in `StarterGui`, including any `LocalScript` inside it. A server `Script` cannot see a player's `PlayerGui`: `player.PlayerGui` is `nil` there. With `ResetOnSpawn` on (the default), a `ScreenGui` is replaced with a fresh copy from `StarterGui` each time the player's character respawns, so changes the script made to it are lost.

## Size and position

`Size` and `Position` are [`UDim2`](../reference/datatypes/udim2.md) values: a fraction of the parent plus a number of pixels, for each axis.

```luau
frame.Size = UDim2.new(0.5, 0, 0, 100)  -- half the parent's width, 100 pixels tall
frame.Position = UDim2.fromScale(0.5, 0.5)
frame.AnchorPoint = Vector2.new(0.5, 0.5) -- position the centre of the frame
```

`AnchorPoint` chooses which point of the object `Position` refers to. `(0, 0)` is the top left and `(0.5, 0.5)` is the centre.

## Text and images

```luau
label.Text = "Score: 0"
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.TextSize = 24
label.TextXAlignment = Enum.TextXAlignment.Left
label.Font = Enum.Font.Mono

image.Image = 1234567       -- the asset id of the image (see Meshes & Textures)
image.ScaleType = Enum.ScaleType.Fit
```

An `ImageLabel` draws nothing until `Image` is set to the asset id of an [uploaded image](meshes-and-textures.md). `ScaleType` is `Stretch` to fill the box, `Fit` to keep the aspect ratio inside it, `Crop` to fill it and trim the image, `Tile` to repeat it at `TileSize`, or `Slice` to stretch only the middle of the image so a bordered panel keeps its corners.

## Layout

A [`CanvasGroup`](../reference/classes/canvas-group.md) is a frame whose `GroupTransparency` fades everything inside it at once. [`UIListLayout`](../reference/classes/ui-list-layout.md) stacks the children of a frame in a row or column, and ignores their `Position`. [`UIGridLayout`](../reference/classes/ui-grid-layout.md) lays them out in a wrapping grid of equal cells. [`UIPadding`](../reference/classes/ui-padding.md) insets the children, [`UICorner`](../reference/classes/ui-corner.md) rounds the corners, [`UIGradient`](../reference/classes/ui-gradient.md) fades the colour and transparency along a line, [`UIStroke`](../reference/classes/ui-stroke.md) draws an outline, and [`UIScale`](../reference/classes/ui-scale.md) scales the object and everything in it, [`UISizeConstraint`](../reference/classes/ui-size-constraint.md) clamps its size, [`UIAspectRatioConstraint`](../reference/classes/ui-aspect-ratio-constraint.md) keeps its proportions, and [`UITextSizeConstraint`](../reference/classes/ui-text-size-constraint.md) limits its text size. Put them inside the object they change.

A [`TextBox`](../reference/classes/text-box.md) lets the player type; read its `Text` when `FocusLost` fires. A [`ScrollingFrame`](../reference/classes/scrolling-frame.md) is a frame with a larger canvas that scrolls with the mouse wheel or its scroll bar. Set `AutomaticCanvasSize` to `Y` and add a `UIListLayout` to make a scrolling list that grows with its content.

Children are clipped to their parent only when `ClipsDescendants` is `true`. Siblings are drawn in order of `ZIndex`, and in the order they were created when `ZIndex` is equal. An object with `Visible` set to `false` hides everything inside it, and so does a `ScreenGui` with `Enabled` set to `false`.

## Responding to input

```luau
local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
local button = playerGui.Hud.Frame.TextButton

button.MouseButton1Click:Connect(function()
    print("clicked")
end)

button.MouseEnter:Connect(function(x, y)
    print("pointer entered at", x, y)
end)
```

| Signal | Passes |
| --- | --- |
| `MouseButton1Click`, `MouseButton2Click` | nothing |
| `Activated` | an `InputObject` and `0` |
| `MouseButton1Down`, `MouseButton1Up`, `MouseButton2Down`, `MouseButton2Up` | `x, y`, the pointer position within the object |
| `MouseEnter`, `MouseLeave` | `x, y` |
| `MouseMoved`, `MouseWheelForward`, `MouseWheelBackward` | `x, y` |
| `InputBegan`, `InputEnded` | an `InputObject` with `UserInputType` `MouseButton1` or `MouseButton2` and `Position` |
| `InputChanged` | an `InputObject`: `MouseMovement` with `Delta` since the last frame, or `MouseWheel` with `Position.Z` of `1` forward and `-1` backward |

The pointer signals (`MouseMoved`, `MouseWheelForward`, `MouseWheelBackward`, `InputBegan`, `InputEnded` and `InputChanged`) fire for every visible object under the pointer, not only the top one and not only objects with `Active` set, so a script can track the mouse over a whole panel. Only mouse input is reported, not keyboard keys, and `x, y` and `Position` are screen pixels. Unlike a `UserInputService` signal they pass only the `InputObject`, with no `gameProcessed` flag.

A click needs the button to be pressed and released on the same object. Releasing somewhere else fires `Up` but not `Click`. `Activated` fires for the left button only. Only buttons and objects with `Active` set to `true` receive input, and clicks on empty screen pass through to the game. When `ScreenGui`s overlap, the one with the higher `DisplayOrder` receives input first.

## Styling GUIs

These pieces combine to build the chunky panel, button and badge look common in simulator and tycoon games.

- **Panels and buttons from one image.** Set `ScaleType` to `Slice` and `SliceCenter` to a [`Rect`](../reference/datatypes/rect.md) holding the stretchable middle of the picture. The corners keep their shape at any size, and `SliceScale` scales them. Use `Tile` with `TileSize` for repeating patterns, and `ImageRectOffset` with `ImageRectSize` to pick one icon out of a sheet. A `UICorner` rounds `Stretch`, `Fit` and `Crop` images, but not `Tile` or `Slice`;
- **Outlines.** [`UIStroke`](../reference/classes/ui-stroke.md) outlines a frame, or the text of a label. For heavy text outlines use a thick stroke in a dark colour. `Enabled` switches it off without removing it;
- **Shine and fades.** A [`UIGradient`](../reference/classes/ui-gradient.md) inside a button darkens its lower half with a two-key `ColorSequence` at `Rotation` `90`. It multiplies the colour the object already has, so a white image or frame takes the gradient colours directly;
- **Tilt.** `Rotation` turns any object and everything inside it around its centre. Small tilts of 5 to 15 degrees suit badges and ribbons. Tween it for a wobble;
- **Fading a whole menu.** Make the panel a [`CanvasGroup`](../reference/classes/canvas-group.md) and tween its `GroupTransparency` between `1` and `0`. Combine it with a tween of a [`UIScale`](../reference/classes/ui-scale.md) for a pop-in;
- **Hover and press art.** On an [`ImageButton`](../reference/classes/image-button.md), `HoverImage` and `PressedImage` swap in other pictures;
- **Fitting any screen.** Give the main panel a [`UIAspectRatioConstraint`](../reference/classes/ui-aspect-ratio-constraint.md) and a [`UISizeConstraint`](../reference/classes/ui-size-constraint.md), size its children with `Scale`, and use [`UIGridLayout`](../reference/classes/ui-grid-layout.md) inside a `ScrollingFrame` with `AutomaticCanvasSize` for item grids;
- **Text.** `RichText` allows `<b>`, `<i>`, `<font color="...">` and similar tags, and `UITextSizeConstraint` keeps `TextScaled` text readable.

```luau
local button = Instance.new("ImageButton")
button.Size = UDim2.new(0, 160, 0, 56)
button.Image = 123456789
button.ScaleType = Enum.ScaleType.Slice
button.SliceCenter = Rect.new(24, 24, 40, 40)
button.Parent = screenGui

local shine = Instance.new("UIGradient")
shine.Color = ColorSequence.new(Color3.new(1, 1, 1), Color3.new(0.74, 0.74, 0.74))
shine.Rotation = 90
shine.Parent = button
```

## GUIs in the world

A [`BillboardGui`](../reference/classes/billboard-gui.md) inside a part shows its contents on screen at that part's position in the world. A [`SurfaceGui`](../reference/classes/surface-gui.md) inside a part draws its contents on one face of the part. Both have `Active`, `Enabled`, `AlwaysOnTop`, and `MaxDistance`.

## Setting properties

Properties check their values. Assigning the wrong type, for example a number to `Size`, raises an error. Colours are clamped to the 0 to 1 range, `Text` is cut off at 2000 characters, and pixel offsets are whole numbers.
