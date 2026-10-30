---
title: Enum
description: The runtime enum namespace.
---

> [!Summary]
> `Enum` provides named groups of constants, such as `Enum.KeyCode` and `Enum.Material`. Each item converts to its `Enum.<group>.<item>` string form.

### EasingDirection

`In`, `InOut`, `Out`

### EasingStyle

`Back`, `Bounce`, `Circular`, `Cubic`, `Elastic`, `Exponential`, `Linear`, `Quad`, `Quart`, `Quint`, `Sine`

### KeyCode

`A`, `B`, `BackSlash`, `Backquote`, `Backspace`, `C`, `Comma`, `D`, `Delete`, `Down`, `E`, `Eight`, `Equals`, `Escape`, `F`, `F1`, `F10`, `F11`, `F12`, `F2`, `F3`, `F4`, `F5`, `F6`, `F7`, `F8`, `F9`, `Five`, `Four`, `G`, `H`, `I`, `J`, `K`, `L`, `Left`, `LeftAlt`, `LeftBracket`, `LeftControl`, `LeftShift`, `LeftSuper`, `M`, `Minus`, `N`, `Nine`, `O`, `One`, `P`, `Period`, `Q`, `Quote`, `R`, `Return`, `Right`, `RightAlt`, `RightBracket`, `RightControl`, `RightShift`, `RightSuper`, `S`, `Semicolon`, `Seven`, `Six`, `Slash`, `Space`, `T`, `Tab`, `Three`, `Two`, `U`, `Unknown`, `Up`, `V`, `W`, `X`, `Y`, `Z`, `Zero`

### Font

`Bangers`, `Figtree`, `Fredoka`, `Lora`, `Mono`, `Oswald`, `Pacifico`, `PressStart2P`, `Roboto`

### FontStyle

`Italic`, `Normal`

### FontWeight

`Bold`, `ExtraBold`, `ExtraLight`, `Heavy`, `Light`, `Medium`, `Regular`, `SemiBold`, `Thin`

### Material

`Brick`, `Grass`, `Ice`, `Metal`, `Paint`, `Plastic`, `Sand`, `Smooth`, `Wood`

### NormalId

`Back`, `Bottom`, `Front`, `Left`, `Right`, `Top`

### PlaybackState

`Begin`, `Cancelled`, `Completed`, `Delayed`, `Paused`, `Playing`

### TextFilterContext

`PrivateChat`, `PublicChat`

### UserInputType

`Focus`, `Gamepad1`, `Keyboard`, `MouseButton1`, `MouseButton2`, `MouseButton3`, `MouseMovement`, `MouseWheel`, `None`, `Touch`

## EnumType Methods

Each enum group, such as `Enum.KeyCode`, exposes these lookup methods.

### FromName()

> [`EnumItem`](../datatypes/enumitem.md) | `nil`
>
> `enumType:FromName(name: string)`
>
> Returns the item with the given name, or `nil` when the name is not part of the enum group.

### FromValue()

> [`EnumItem`](../datatypes/enumitem.md)
>
> `enumType:FromValue(value: Number)`
>
> Returns the item with the given integral value.

### GetEnumItems()

> `{ EnumItem }`
>
> `enumType:GetEnumItems()`
>
> Returns a table containing the items in the enum group.
