---
title: NumberSequence
description: A number that changes along a line, defined by keypoints.
---

## Summary

A `NumberSequence` blends between numbers from `0` to `1` along a line. It is made of [`NumberSequenceKeypoint`](#numbersequencekeypoint)s, and it is the type of the `Transparency` property of a gradient.

```lua
local fade = NumberSequence.new({
	NumberSequenceKeypoint.new(0, 0),
	NumberSequenceKeypoint.new(0.7, 0),
	NumberSequenceKeypoint.new(1, 1),
})
```

## Constructors

- `NumberSequence.new(value: number)` - one number all the way along;
- `NumberSequence.new(value0: number, value1: number)` - blends from the first to the second;
- `NumberSequence.new(keypoints: {NumberSequenceKeypoint})` - between 2 and 20 keypoints. The first must be at time `0`, the last at time `1`, and times must not go backwards.

## Properties

- `Keypoints` - the list of keypoints.

## Methods

- `Lerp(goal: NumberSequence, alpha: number)` - blends keypoint by keypoint when both have the same number of keypoints. Otherwise it returns `self` below `alpha` of `0.5` and `goal` from there.

`==` compares two sequences keypoint by keypoint.

## NumberSequenceKeypoint

`NumberSequenceKeypoint.new(time: number, value: number, envelope: number)` has `Time`, from `0` to `1`, `Value`, and `Envelope`, which defaults to `0`. GUI gradients only use `Value`.
