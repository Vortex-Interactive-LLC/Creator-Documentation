---
title: Meshes & Textures
description: Upload models and images, then use them in Studio.
---
Custom models and images are uploaded as assets. Each upload gets a numeric asset id, which you use in Studio or in a script. Scripts cannot create meshes or textures: `Instance.new` does not support `MeshPart`, `Texture`, `Decal` or `SurfaceAppearance`, so place models in Studio and only change their other properties from scripts.

## Uploading a model

Upload models on [Vortex Create](https://create.playvortex.io/models).

- File types: `.glb`, `.obj` and `.fbx`;
- At most 20 MB and 20,000 triangles;
- Static models only. Animated or rigged models are rejected;
- A `.glb` must be a single self-contained file, with its textures embedded and no external files or extensions.

A `.obj` model can be uploaded together with its `.mtl` file and texture images. If a model needs a texture that is not included, the upload asks for it. Textures are limited to 5 MB and are shrunk to fit 2048 x 2048. Uploads are reviewed before they can be used.

## Uploading an image

Upload images on [Vortex Create](https://create.playvortex.io/images) as well.

- PNG, JPG or WEBP files, but not animated ones;
- At most 5 MB, converted to PNG and shrunk to fit 2048 x 2048;
- Up to 50 images per account.

Models, their textures and images share a 64 MB storage limit per account.

## Using a model in Studio

Add a `MeshPart`, select it, and set `MeshId` in the Model section of the Properties panel to the asset id. Studio checks that the asset exists, is a model, and is available to you, then resizes the part to the model's proportions. If the id is wrong or belongs to an image, Studio shows an error instead.

`CollisionFidelity` chooses the collision shape: `Default`, `Hull`, `Box` or `Precise`.

## Using an image

Images go anywhere a GUI takes an image. Set `ImageLabel.Image` to the asset id. See [Building GUIs](gui.md).

```luau
imageLabel.Image = 1234567
```

## Textures on parts

A `Texture` added to a part in Studio draws a pattern on one of its faces. Only the built-in `Inlets` and `Studs` patterns are available. See [`Texture`](../reference/classes/texture.md).
