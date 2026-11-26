---
title: Lighting Effects
description: Change the mood of a place with bloom, blur, color grading, sky, haze, and highlights.
---
Lighting effects are children of `Lighting`. Add them in Studio from the `Lighting` entry in the Explorer, or from a script.

```luau
local bloom = Instance.new("BloomEffect")
bloom.Intensity = 0.6
bloom.Parent = game:GetService("Lighting")
```

## Screen effects

- [`BloomEffect`](../reference/classes/bloom-effect.md) makes bright areas glow;
- [`ColorCorrectionEffect`](../reference/classes/color-correction-effect.md) changes `Brightness`, `Contrast`, `Saturation`, and `TintColor`. Several of them add together;
- [`DepthOfFieldEffect`](../reference/classes/depth-of-field-effect.md) blurs what is far from `FocusDistance`;
- [`BlurEffect`](../reference/classes/blur-effect.md) blurs the whole screen, for menus and fades;
- [`SunRaysEffect`](../reference/classes/sun-rays-effect.md) draws light shafts from the sun.

Bloom and depth of field only draw at the highest graphics quality. Blur and sun rays draw on every backend except OpenGL. Color correction works everywhere.

```luau
local TweenService = game:GetService("TweenService")

local blur = Instance.new("BlurEffect")
blur.Size = 0
blur.Parent = game:GetService("Lighting")

TweenService:Create(blur, TweenInfo.new(0.5), { Size = 24 }):Play()
```

## Sky

A [`Sky`](../reference/classes/sky.md) changes the stars and celestial bodies, and can replace the sky with a skybox made of six images.

```luau
local sky = Instance.new("Sky")
sky.StarCount = 1500
sky.CelestialBodiesShown = false
sky.Parent = game:GetService("Lighting")
```

Set `SkyboxBk`, `SkyboxDn`, `SkyboxFt`, `SkyboxLf`, `SkyboxRt`, and `SkyboxUp` to image asset ids for a skybox. Faces you leave empty show the built-in sky.

## Atmosphere

An [`Atmosphere`](../reference/classes/atmosphere.md) fades distant parts into haze, and replaces the `FogStart`, `FogEnd`, and `FogColor` settings while it exists. Raise `Density` to bring the haze closer.

```luau
local atmosphere = Instance.new("Atmosphere")
atmosphere.Density = 0.3
atmosphere.Color = Color3.fromRGB(190, 200, 220)
atmosphere.Parent = game:GetService("Lighting")
```

## Highlight

A [`Highlight`](../reference/classes/highlight.md) outlines and tints a part or model. It does not go in `Lighting`: parent it to what it should mark, or set `Adornee`.

```luau
local highlight = Instance.new("Highlight")
highlight.FillColor = Color3.fromRGB(255, 200, 0)
highlight.OutlineColor = Color3.new(1, 1, 1)
highlight.DepthMode = Enum.HighlightDepthMode.Occluded
highlight.Parent = workspace.Statue
```

`AlwaysOnTop` shows it through walls and `Occluded` hides it behind other parts.
