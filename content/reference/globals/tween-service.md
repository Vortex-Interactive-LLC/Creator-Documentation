---
title: TweenService
description: Global alias for the TweenService animation service.
---
# TweenService

Get the service through either global alias:

```luau
local tweenService = TweenService
-- or
local tweenService = game:GetService("TweenService")
```

See the [TweenService reference](../classes/tween-service.md) for `Create` and the current Vortex Studio behavior notes.

TweenService allows you to smoothly change supported properties of an object over a specified amount of time. You can also control how the property changes using different easing styles and directions.

You can access TweenService using the `game:GetService()` function:

    local TweenService = game:GetService("TweenService")

Now, let's create a simple tween that moves a part.

### Getting the Part

    local TweenService = game:GetService("TweenService") -- Get TweenService

    local part = workspace:FindFirstChild("TweenPart")

This gets TweenService and finds a part named `TweenPart` inside the `Workspace`.

You can use any valid object that supports the properties you want to tween. You can also create an object using [Instance.new](../globals/instance-new.md).

### Creating TweenInfo

    local tweenInfo = TweenInfo.new(
        2,
        Enum.EasingStyle.Linear,
        Enum.EasingDirection.Out
    )

`TweenInfo` defines how the tween behaves.

The values above specify:

- `2` — The duration of the tween in seconds.
- `Enum.EasingStyle.Linear` — The easing style used by the tween.
- `Enum.EasingDirection.Out` — The easing direction.

You can find the available easing styles and directions on the [Enum](./enum.md) page.

### Creating the Tween Goal

    local tweenGoal = {
        Position = Vector3.new(0, 5, 0),
        Color = Color3.fromRGB(137, 111, 255)
    }

The `tweenGoal` table contains the properties and values that the tween will change.

In this example, the part's `Position` is changed to `Vector3.new(0, 5, 0)` and its `Color` is changed to the classic Vortex purple.

Other supported properties can also be tweened, such as `Transparency`, depending on the object and property.

### Creating and Playing the Tween

    local tween = TweenService:Create(part, tweenInfo, tweenGoal)

    tween:Play()

`TweenService:Create()` creates a tween using the object, `TweenInfo`, and goal table defined above.

Calling `tween:Play()` starts the tween, smoothly applying the specified property changes over the configured duration.

> [!NOTE]
> The properties being tweened must support interpolation. Unsupported properties cannot be changed using TweenService.
