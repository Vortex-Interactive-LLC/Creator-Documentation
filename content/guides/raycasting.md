---
title: Raycasting
description: Find what is in front of a point by casting a ray.
---
`workspace:Raycast(origin, direction, params)` fires an invisible ray and tells you the first thing it hits.

```luau
local origin = Vector3.new(0, 5, 0)
local direction = Vector3.new(0, 0, -40)

local result = workspace:Raycast(origin, direction)
if result then
    print("hit", result.Instance.Name, "at", result.Position)
end
```

`direction` is a vector, and its length is the distance the ray travels. In this example the ray reaches 40 studs. Returning `nil` means nothing was hit. A zero-length direction raises an error.

## The result

A [`RaycastResult`](../reference/datatypes/raycast-result.md) has:

- `Instance` - the part that was hit;
- `Position` - the point of impact;
- `Normal` - the direction the surface faces at that point;
- `Distance` - how far the ray travelled before hitting;
- `Material` - the material of the part.

## Ignoring or limiting what is hit

Pass a [`RaycastParams`](../reference/datatypes/raycast-params.md) table as the third argument. It is an ordinary table with two fields.

```luau
local params = {
    FilterDescendantsInstances = { workspace.Wall, player.Character },
    FilterType = "Exclude",
}

local result = workspace:Raycast(origin, direction, params)
```

With `"Exclude"` the listed instances and their descendants are ignored. With `"Include"` only they can be hit. The field names are exact: `ExcludeInstances` and `IncludeInstances` are not recognised and have no effect.

## Casting from the camera

In a `LocalScript`, combine a ray from the camera with `Raycast` to find what the cursor points at. See [Mouse & Camera](mouse-and-camera.md).

> [!NOTE]
> `workspace:Spherecast` and `workspace:Blockcast` exist, but calling them from a server `Script` currently raises `Cast is not supported on the game server yet`.
