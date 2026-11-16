---
title: ColorSequence
description: A colour that changes along a line, defined by keypoints.
---

## Summary

A `ColorSequence` blends between colours from `0` to `1` along a line. It is made of [`ColorSequenceKeypoint`](#colorsequencekeypoint)s, and it is the type of the `Color` property of a gradient.

```lua
local sequence = ColorSequence.new({
	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 200, 60)),
	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 90, 30)),
})
```

## Constructors

- `ColorSequence.new(color: Color3)` - one colour all the way along;
- `ColorSequence.new(color0: Color3, color1: Color3)` - blends from the first to the second;
- `ColorSequence.new(keypoints: {ColorSequenceKeypoint})` - between 2 and 20 keypoints. The first must be at time `0`, the last at time `1`, and times must not go backwards.

## Properties

- `Keypoints` - the list of keypoints.

## Methods

- `Lerp(goal: ColorSequence, alpha: number)` - blends keypoint by keypoint when both have the same number of keypoints. Otherwise it returns `self` below `alpha` of `0.5` and `goal` from there.

`==` compares two sequences keypoint by keypoint.

## ColorSequenceKeypoint

`ColorSequenceKeypoint.new(time: number, color: Color3)` has `Time`, from `0` to `1`, and `Value`, the [`Color3`](./color3.md) at that time.
