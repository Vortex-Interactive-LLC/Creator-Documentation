---
title: Particles
description: Add fire, smoke, sparks, and custom particle effects to parts.
---
Particle effects are instances you parent to a part or an `Attachment`. They draw on the client, never collide, and do not need a script to run.

## Ready-made effects

`Fire`, `Smoke`, and `Sparkles` are one-line effects. Parent them to a part and they start.

```luau
local fire = Instance.new("Fire")
fire.Size = 8
fire.Heat = 12
fire.Parent = workspace.Torch
```

See [`Fire`](../reference/classes/fire.md), [`Smoke`](../reference/classes/smoke.md), and [`Sparkles`](../reference/classes/sparkles.md). Set `Enabled` to `false` to stop one without removing it.

## ParticleEmitter

A [`ParticleEmitter`](../reference/classes/particle-emitter.md) gives full control. A particle starts with a random lifetime, speed, and direction from its ranges, then changes size, color, and transparency over its life.

```luau
local emitter = Instance.new("ParticleEmitter")
emitter.Rate = 30
emitter.Lifetime = NumberRange.new(1, 2)
emitter.Speed = NumberRange.new(4, 8)
emitter.SpreadAngle = Vector2.new(25, 25)
emitter.Size = NumberSequence.new(1.5, 0)
emitter.Transparency = NumberSequence.new(0, 1)
emitter.Color = ColorSequence.new(Color3.new(1, 0.7, 0.2), Color3.new(1, 0.1, 0))
emitter.LightEmission = 1
emitter.Parent = workspace.Part
```

- `NumberRange.new(min, max)` picks a random value between the two for each particle;
- `NumberSequence` and `ColorSequence` run from the start to the end of a particle's life, so `NumberSequence.new(1.5, 0)` shrinks a particle to nothing;
- `LightEmission` of `1` adds the color to what is behind it, which suits fire and magic. `0` blends normally, which suits smoke and dust;
- `Acceleration` and `Drag` bend the path. An upward `Acceleration` makes smoke rise;
- `Texture` takes the asset id of an uploaded image. Without one, particles are soft round dots.

## Bursts

`Emit(count)` spawns particles at once, which suits impacts and pickups. Turn `Enabled` off so only bursts show.

```luau
emitter.Enabled = false
part.Touched:Connect(function()
	emitter:Emit(30)
end)
```

`Clear()` removes every live particle.

## Moving parts

By default, particles stay where they were born when the part moves, which leaves a trail. Set `LockedToPart` to `true` to carry them along, or raise `VelocityInheritance` to pass some of the part's speed to new particles.

## Explosions

An [`Explosion`](../reference/classes/explosion.md) plays a fireball and also pushes parts and breaks joints. Only the server runs the blast.

```luau
local explosion = Instance.new("Explosion")
explosion.Position = Vector3.new(0, 10, 0)
explosion.BlastRadius = 12
explosion.Parent = workspace
```

## Limits

- Each emitter shows at most about 1000 particles at once. Very high `Rate` and `Lifetime` values are capped;
- Lower graphics quality shows fewer particles;
- `ShapePartial` and `LightInfluence` are saved but do not change the picture yet.
