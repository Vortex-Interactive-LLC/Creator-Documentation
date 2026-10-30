---
title: Tweening
description: Animate properties smoothly over time with TweenService.
---
`TweenService` changes properties of an instance gradually instead of instantly. It works in both `Script` and `LocalScript`.

## A first tween

```luau
local TweenService = game:GetService("TweenService")

local part = workspace:WaitForChild("TweenPart")

local info = TweenInfo.new(2, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
local goal = { Position = Vector3.new(0, 10, 0) }

local tween = TweenService:Create(part, info, goal)
tween:Play()
```

`TweenInfo.new(time, easingStyle, easingDirection, repeatCount, reverses, delayTime)` describes how the tween plays. Every argument is optional. The defaults are one second with `Enum.EasingStyle.Quad` and `Enum.EasingDirection.Out`. See [`TweenInfo`](../reference/datatypes/tween-info.md) and the available styles in [`Enum`](../reference/globals/enum.md).

The goal table lists the properties to change and the values to reach. `Position`, `Size`, `CFrame`, `Transparency`, and `Color` are supported on parts.

## Controlling a tween

```luau
tween:Play()
tween:Pause()   -- keeps the current values
tween:Play()    -- resumes from where it paused
tween:Cancel()  -- stops where it is
```

`tween.PlaybackState` is an `Enum.PlaybackState`: `Begin` before it has played, `Playing`, `Paused`, `Completed`, and `Cancelled`.

## Waiting for the end

`tween.Completed` fires when the tween finishes or is cancelled, and passes the final playback state.

```luau
tween.Completed:Connect(function(state)
    if state == Enum.PlaybackState.Completed then
        print("reached the goal")
    else
        print("stopped early")
    end
end)
```

> [!NOTE]
> A property name that is not supported does not raise an error when you call `Create`. The tween is created, but that property is not changed. Check the spelling of property names if a tween appears to do nothing.

See the [`TweenService`](../reference/classes/tween-service.md) and [`Tween`](../reference/datatypes/tween.md) reference.
