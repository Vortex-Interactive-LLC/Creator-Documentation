---
title: CornerWedgePart
description: A corner wedge-shaped part.
---

## Summary

`Instance.new("CornerWedgePart")` creates a [`Part`](./part.md) whose `Shape` is `Enum.PartType.CornerWedge`. It has the same default size (`4, 1, 2`), is anchored, and has all of the properties and methods of a `Part`.

```lua
local wedge = Instance.new("CornerWedgePart")
wedge.Position = Vector3.new(0, 5, 0)
wedge.Parent = workspace

print(wedge.ClassName) --> Part
print(wedge.Shape)     --> Enum.PartType.CornerWedge
```

Its `ClassName` is `"Part"`, so use `Shape` to tell it apart from a block.
