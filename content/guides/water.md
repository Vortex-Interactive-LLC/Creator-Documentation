---
title: Water
description: Place water in Studio, and set how it looks and how players and parts behave in it.
---
Water is a box you place in Studio. Everything inside the box is under water: players swim, loose parts float, and the camera gets an underwater view when it goes below the surface.

```luau
-- LocalScript
local player = game:GetService("Players").LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

while task.wait(0.5) do
    if humanoid:GetState() == Enum.HumanoidStateType.Swimming then
        print("swimming")
    end
end
```

## Adding water

In Studio, open the Part dropdown and choose `Water`. A box of water, 64 studs wide, 16 studs tall, and 64 studs deep, is added to the world. Move, rotate, and resize it like a part. Its top face is the surface and its bottom is the floor.

The water box does not collide.

> [!NOTE]
> A rotated water box is treated as the box that fits around it, so water is always level and axis aligned.

## Changing how it looks

Select `Terrain` in the Explorer. Its properties control every body of water in the game at once: `WaterColor`, `WaterReflectance`, `WaterTransparency`, `WaterWaveSize`, and `WaterWaveSpeed`. See [`Terrain`](../reference/classes/terrain.md) for the ranges.

Water gets darker the deeper it is. The depth is read from the parts under the water, so build the seabed with normal parts.

## Swimming

A character swims when it is deep enough in water. In a `LocalScript`, `humanoid:GetState()` returns `Enum.HumanoidStateType.Swimming` while it does.

- Movement follows the camera direction, so looking down and moving swims downward;
- The jump key swims upward;
- At the surface the character floats and cannot swim above it.

Swimming is worked out on each player's own machine, and other players see the swim animation on your character. A server `Script` does not see the `Swimming` state yet.

## Floating parts

Parts that are not anchored float in water. A part that is partly under the surface is pushed up and slowed down, so a crate bobs and drifts. Anchored parts do not move.

## Under the surface

When the camera is under water, the sky is hidden and the view is tinted and fogged. The effect is on while the camera is below the surface, not while the character is, so a camera above the water looking down sees the water from outside.

## Limits

- Scripts cannot create water or change the `Terrain` settings. Place water in Studio;
- Every water box has the same look;
- Water does not affect `Part.Touched` or raycasts.
