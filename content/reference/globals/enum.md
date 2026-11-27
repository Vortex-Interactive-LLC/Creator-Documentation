---
title: Enum
description: The runtime enum namespace.
---

> [!Summary]
> `Enum` provides named groups of constants, such as `Enum.KeyCode` and `Enum.Material`. Each item converts to its `Enum.<group>.<item>` string form.

### ActuatorRelativeTo

`Attachment0`, `Attachment1`, `World`

### ApplyStrokeMode

`Border`, `Contextual`

### AspectType

`FitWithinMaxSize`, `ScaleWithParentSize`

### AssetFetchStatus

`Failure`, `Success`, `TimedOut`

### AssetType

`Face`, `FaceAccessory`, `Hair`, `Hat`, `Other`, `Pants`, `Shirt`

### AssetTypeVerification

`Always`, `ClientOnly`, `Default`

### AutomaticCanvasSize

`None`, `X`, `XY`, `Y`

### AutomaticSize

`None`, `X`, `XY`, `Y`

### AvatarAnimation

`Backflip`, `Climb`, `ClubPenguin`, `EeveeDance`, `Fall`, `Headless`, `Idle`, `Jump`, `Sit`, `Sturdy`, `Swim`, `SwimIdle`, `Walk`, `Wave`

### BodyType

`Female`, `Male`

### CameraMode

`Classic`, `LockFirstPerson`

### CameraType

`Attach`, `Custom`, `Fixed`, `Follow`, `Orbital`, `Scriptable`, `Track`, `Watch`

### CollisionFidelity

`Box`, `Default`, `Hull`, `PreciseConvexDecomposition`, `Tunable`

### ControlMode

`Classic`, `MouseLockSwitch`

### DataStoreRequestType

`GetAsync`, `GetSortedAsync`, `GetVersionAsync`, `ListAsync`, `OnUpdate`, `OrderedList`, `OrderedRead`, `OrderedRemove`, `OrderedWrite`, `RemoveVersionAsync`, `SetIncrementAsync`, `SetIncrementSortedAsync`, `StandardList`, `StandardRead`, `StandardRemove`, `StandardWrite`, `UpdateAsync`

### DominantAxis

`Height`, `Width`

### EasingDirection

`In`, `InOut`, `Out`

### EasingStyle

`Back`, `Bounce`, `Circular`, `Cubic`, `Elastic`, `Exponential`, `Linear`, `Quad`, `Quart`, `Quint`, `Sine`

### FillDirection

`Horizontal`, `Vertical`

### Font

`Bangers`, `Figtree`, `Fredoka`, `Lora`, `Mono`, `Oswald`, `Pacifico`, `PressStart2P`, `Roboto`

### FontStyle

`Italic`, `Normal`

### FontWeight

`Bold`, `ExtraBold`, `ExtraLight`, `Heavy`, `Light`, `Medium`, `Regular`, `SemiBold`, `Thin`

### GradientInterpolation

`Perceptual`, `Rgb`

### HorizontalAlignment

`Center`, `Left`, `Right`

### HumanoidDisplayDistanceType

`None`, `Subject`, `Viewer`

### HumanoidHealthDisplayType

`AlwaysOff`, `AlwaysOn`, `DisplayWhenDamaged`

### HumanoidStateType

`Climbing`, `Dead`, `FallingDown`, `Flying`, `Freefall`, `GettingUp`, `Jumping`, `Landed`, `None`, `Physics`, `PlatformStanding`, `Ragdoll`, `Running`, `RunningNoPhysics`, `Seated`, `StrafingNoPhysics`, `Swimming`

### InfoType

`Asset`, `GamePass`

### KeyCode

`A`, `B`, `BackSlash`, `Backquote`, `Backspace`, `C`, `Comma`, `D`, `Delete`, `Down`, `E`, `Eight`, `Equals`, `Escape`, `F`, `F1`, `F10`, `F11`, `F12`, `F2`, `F3`, `F4`, `F5`, `F6`, `F7`, `F8`, `F9`, `Five`, `Four`, `G`, `H`, `I`, `J`, `K`, `L`, `Left`, `LeftAlt`, `LeftBracket`, `LeftControl`, `LeftShift`, `LeftSuper`, `M`, `Minus`, `N`, `Nine`, `O`, `One`, `P`, `Period`, `Q`, `Quote`, `R`, `Return`, `Right`, `RightAlt`, `RightBracket`, `RightControl`, `RightShift`, `RightSuper`, `S`, `Semicolon`, `Seven`, `Six`, `Slash`, `Space`, `T`, `Tab`, `Three`, `Two`, `U`, `Unknown`, `Up`, `V`, `W`, `X`, `Y`, `Z`, `Zero`

### LineJoinMode

`Bevel`, `Miter`, `Round`

### Material

`Brick`, `Carpet`, `Concrete`, `DiamondPlate`, `Grass`, `Ice`, `Metal`, `Neon`, `Paint`, `Plastic`, `Sand`, `Smooth`, `Wood`

### MouseBehavior

`Default`, `LockCenter`, `LockCurrentPosition`

### NormalId

`Back`, `Bottom`, `Front`, `Left`, `Right`, `Top`

### PartType

`Ball`, `Block`, `CornerWedge`, `Cylinder`, `Mesh`, `Wedge`

### PlaybackState

`Begin`, `Cancelled`, `Completed`, `Delayed`, `Paused`, `Playing`

### PreferredTextSize

`Large`, `Larger`, `Largest`, `Medium`

### PurchaseResult

`Cancelled`, `Expired`, `InsufficientFunds`, `Owned`, `PriceChanged`, `Purchased`, `Unavailable`

### RaycastFilterType

`Exclude`, `Include`

### ResamplerMode

`Default`, `Pixelated`

### RotationType

`CameraRelative`, `MovementRelative`

### ScaleType

`Crop`, `Fit`, `Slice`, `Stretch`, `Tile`

### ScrollingDirection

`X`, `XY`, `Y`

### SortOrder

`Custom`, `LayoutOrder`, `Name`

### StartCorner

`BottomLeft`, `BottomRight`, `TopLeft`, `TopRight`

### SurfaceGuiSizingMode

`FixedSize`, `PixelsPerStud`

### SurfaceType

`Inlet`, `Smooth`, `Studs`

### TextFilterContext

`PrivateChat`, `PublicChat`

### TextTruncate

`AtEnd`, `None`

### TextXAlignment

`Center`, `Left`, `Right`

### TextYAlignment

`Bottom`, `Center`, `Top`

### UserInputState

`Begin`, `Cancel`, `Change`, `End`, `None`

### UserInputType

`Accelerometer`, `Focus`, `Gamepad1`, `Gamepad2`, `Gamepad3`, `Gamepad4`, `Gamepad5`, `Gamepad6`, `Gamepad7`, `Gamepad8`, `Gyro`, `InputMethod`, `Keyboard`, `MouseButton1`, `MouseButton2`, `MouseButton3`, `MouseMovement`, `MouseWheel`, `None`, `TextInput`, `Touch`

### VerticalAlignment

`Bottom`, `Center`, `Top`

### ZIndexBehavior

`Global`, `Sibling`

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
