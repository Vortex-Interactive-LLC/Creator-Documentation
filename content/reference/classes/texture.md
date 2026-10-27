---
title: Texture
description: Textures allow for rendering special decals onto parts
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of a `Texture`
<br><br>

- [Face](#face): `Enum.Face`
- [Texture](#texture): `Enum.Texture`

</details>

</ul>
</details>

## Overview

This page describes the editor-facing `Texture` concept. Texture scripting is not
currently available in the Vortex runtime; see the testing notes below. When a
texture is added to an editor-authored [`part`](./part.md), its `Face` and name
are set automatically, so six textures can cover the entire part quickly.

## Properties

### Face
> `Texture.Face: Enum.Face`
>
> Controls which face of the parent [`Part`](./part.md) that the texture is displayed on.

### Texture
> `Texture.Texture: Enum.Texture`
>
> Sets which texture to render onto the selected face.

## Testing Notes

In Vortex Studio 0.3.4, `Instance.new("Texture")`,
`Instance.new("Decal")`, and `Instance.new("SurfaceAppearance")` all fail in
both Script and LocalScript. A script-created `Part` also has no readable
`Texture`, `TextureID`, `SurfaceAppearance`, or `Decal` field.

Editor-authored texture behavior was not established by this probe, but there
is currently no confirmed script API for creating or changing textures.
