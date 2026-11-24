---
title: MeshPart
description: A part that has the shape of an uploaded model.
---

## Summary

A `MeshPart` is a [`Part`](./part.md) whose shape comes from an uploaded model, set with `MeshId`. It has every property and method of a `Part`. See [Meshes & Textures](../../guides/meshes-and-textures.md).

## Properties

- `MeshId` - `number`, the asset id of the model. Defaults to `0`, which draws no mesh;
- `TextureID` - `number`, the asset id of the image wrapped on the model. Defaults to `0`;
- `CollisionFidelity` - `Enum.CollisionFidelity`, how closely collisions follow the shape of the model: `Box`, `Hull`, `PreciseConvexDecomposition`, `Default`, or `Tunable`. Defaults to `Default`;
- every property of a [`Part`](./part.md).
