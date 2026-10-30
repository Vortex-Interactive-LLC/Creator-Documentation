---
title: Building GUIs
description: Build on-screen and in-world interfaces and respond to clicks.
---
A GUI is a tree of instances. A [`ScreenGui`](../reference/classes/screen-gui.md) is the root, and objects such as [`Frame`](../reference/classes/frame.md), [`TextLabel`](../reference/classes/text-label.md), [`TextButton`](../reference/classes/text-button.md) and [`ImageLabel`](../reference/classes/image-label.md) go inside it. Anything inside an object is drawn relative to it.

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

Put the `ScreenGui` in `StarterGui`. When a player joins, they get a [`PlayerGui`](../reference/classes/player-gui.md) containing a copy of everything in `StarterGui`, including any `LocalScript` inside it. A server `Script` cannot see a player's `PlayerGui`: `player.PlayerGui` is `nil` there. With `ResetOnSpawn` on (the default), a `ScreenGui` is replaced with a fresh copy from `StarterGui` each time the player's character respawns, so changes the script made to it are lost.

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

image.Image = 1234567       -- the asset id of the image
image.ScaleType = Enum.ScaleType.Fit
```

An `ImageLabel` draws nothing until `Image` is set. `ScaleType` is `Stretch` to fill the box, `Fit` to keep the aspect ratio inside it, or `Crop` to fill it and trim the image.

## Layout

[`UIListLayout`](../reference/classes/ui-list-layout.md) stacks the children of a frame in a row or column, and ignores their `Position`. [`UIPadding`](../reference/classes/ui-padding.md) insets the children, [`UICorner`](../reference/classes/ui-corner.md) rounds the corners, and [`UIStroke`](../reference/classes/ui-stroke.md) draws an outline. Put them inside the object they change.

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

A click needs the button to be pressed and released on the same object. Releasing somewhere else fires `Up` but not `Click`. `Activated` fires for the left button only. Only buttons and objects with `Active` set to `true` receive input, and clicks on empty screen pass through to the game. When `ScreenGui`s overlap, the one with the higher `DisplayOrder` receives input first.

## GUIs in the world

A [`BillboardGui`](../reference/classes/billboard-gui.md) inside a part shows its contents on screen at that part's position in the world. A [`SurfaceGui`](../reference/classes/surface-gui.md) inside a part draws its contents on one face of the part. Both have `Active`, `Enabled`, `AlwaysOnTop` and `MaxDistance`.

## Setting properties

Properties check their values. Assigning the wrong type, for example a number to `Size`, raises an error. Colours are clamped to the 0 to 1 range, `Text` is cut off at 2000 characters, and pixel offsets are whole numbers.
