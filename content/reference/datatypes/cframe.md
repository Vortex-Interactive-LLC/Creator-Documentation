---
title: CFrame
description: A data type that represents both a 3D position and orientation.
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of a `CFrame`.
<br><br>

* [Position](#position): `Vector3`
* [Rotation](#rotation): `CFrame`
* [X](#x), [Y](#y), [Z](#z): `Number`
* [LookVector](#lookvector), [RightVector](#rightvector), [UpVector](#upvector): `Vector3`
* [XVector](#xvector), [YVector](#yvector), [ZVector](#zvector): `Vector3`

</details>

<details>
<summary><b>Constants</b></summary>
Constants of a `CFrame`.
<br><br>

* [identity](#identity): `CFrame`

</details>

<details>
<summary><b>Constructors</b></summary>
Constructors of a `CFrame`.
<br><br>

* [new](#new): `CFrame`
* [Angles](#angles): `CFrame`
* [fromAxisAngle](#fromaxisangle): `CFrame`
* [fromEulerAnglesXYZ](#fromeuleranglesxyz): `CFrame`
* [fromEulerAnglesYXZ](#fromeuleranglesyxz): `CFrame`
* [fromMatrix](#frommatrix): `CFrame`
* [fromOrientation](#fromorientation): `CFrame`
* [lookAt](#lookat): `CFrame`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of a `CFrame`.
<br><br>

* [GetComponents](#getcomponents): `...Number`
* [Inverse](#inverse): `CFrame`
* [Lerp](#lerp): `CFrame`
* [PointToObjectSpace](#pointtoobjectspace): `Vector3`
* [PointToWorldSpace](#pointtoworldspace): `Vector3`
* [ToEulerAnglesXYZ](#toeuleranglesxyz): `Number, Number, Number`
* [ToEulerAnglesYXZ](#toeuleranglesyxz): `Number, Number, Number`
* [ToObjectSpace](#toobjectspace): `CFrame`
* [ToOrientation](#toorientation): `Number, Number, Number`
* [ToWorldSpace](#toworldspace): `CFrame`
* [VectorToObjectSpace](#vectortoobjectspace): `Vector3`
* [VectorToWorldSpace](#vectortoworldspace): `Vector3`

</details>

## Properties

### Position

> `Vector3`
>
> The position component of the CFrame.

<br/>

### Rotation

> `CFrame`
>
> The rotation component of the CFrame, with its position reset to the origin.

<br/>

### X

> `Number`
>
> The X coordinate of the CFrame position.

<br/>

### Y

> `Number`
>
> The Y coordinate of the CFrame position.

<br/>

### Z

> `Number`
>
> The Z coordinate of the CFrame position.

<br/>

### LookVector

> `Vector3`
>
> The normalized forward direction of the CFrame.

<br/>

### RightVector

> `Vector3`
>
> The normalized right direction of the CFrame.

<br/>

### UpVector

> `Vector3`
>
> The normalized up direction of the CFrame.

<br/>

### XVector

> `Vector3`
>
> The X basis vector of the rotation matrix. Equivalent to `RightVector`.

<br/>

### YVector

> `Vector3`
>
> The Y basis vector of the rotation matrix. Equivalent to `UpVector`.

<br/>

### ZVector

> `Vector3`
>
> The Z basis vector of the rotation matrix. Equivalent to `-LookVector`.

<br/>

## Constants

### identity

> `CFrame`
>
> `CFrame.identity`
>
> The CFrame at `(0, 0, 0)` with no rotation.

<br/>

## Constructors

### new

> `CFrame`
>
> `CFrame.new()`
>
> `CFrame.new(position: Vector3)`
>
> `CFrame.new(x: Number, y: Number, z: Number)`
>
> Creates a CFrame at the origin, from a position vector, or from three position coordinates.

#### Parameters

- `position`: `Vector3` — the position of the CFrame.
- `x`: `Number` — the X position.
- `y`: `Number` — the Y position.
- `z`: `Number` — the Z position.

<br/>

### Angles

> `CFrame`
>
> `CFrame.Angles(rotationX: Number, rotationY: Number, rotationZ: Number)`
>
> Creates a CFrame rotated by the supplied angles in radians.

#### Parameters

- `rotationX`: `Number` — the X-axis rotation in radians.
- `rotationY`: `Number` — the Y-axis rotation in radians.
- `rotationZ`: `Number` — the Z-axis rotation in radians.

<br/>

### fromAxisAngle

> `CFrame`
>
> `CFrame.fromAxisAngle(axis: Vector3, angle: Number)`
>
> Creates a CFrame rotated around `axis` by `angle` radians.

#### Parameters

- `axis`: `Vector3` — the axis of rotation.
- `angle`: `Number` — the rotation angle in radians.

<br/>

### fromEulerAnglesXYZ

> `CFrame`
>
> `CFrame.fromEulerAnglesXYZ(rotationX: Number, rotationY: Number, rotationZ: Number)`
>
> Creates a CFrame using Euler rotations in XYZ order.

#### Parameters

- `rotationX`: `Number` — the X-axis rotation in radians.
- `rotationY`: `Number` — the Y-axis rotation in radians.
- `rotationZ`: `Number` — the Z-axis rotation in radians.

<br/>

### fromEulerAnglesYXZ

> `CFrame`
>
> `CFrame.fromEulerAnglesYXZ(rotationX: Number, rotationY: Number, rotationZ: Number)`
>
> Creates a CFrame using Euler rotations in YXZ order.

#### Parameters

- `rotationX`: `Number` — the X-axis rotation in radians.
- `rotationY`: `Number` — the Y-axis rotation in radians.
- `rotationZ`: `Number` — the Z-axis rotation in radians.

<br/>

### fromMatrix

> `CFrame`
>
> `CFrame.fromMatrix(position: Vector3, vX: Vector3, vY: Vector3, vZ: Vector3)`
>
> Creates a CFrame from a position and its three rotation basis vectors.

#### Parameters

- `position`: `Vector3` — the position of the CFrame.
- `vX`: `Vector3` — the X basis vector.
- `vY`: `Vector3` — the Y basis vector.
- `vZ`: `Vector3` — the Z basis vector.

<br/>

### fromOrientation

> `CFrame`
>
> `CFrame.fromOrientation(rotationX: Number, rotationY: Number, rotationZ: Number)`
>
> Creates a CFrame from X, Y, and Z orientation angles in radians.

#### Parameters

- `rotationX`: `Number` — the X-axis rotation in radians.
- `rotationY`: `Number` — the Y-axis rotation in radians.
- `rotationZ`: `Number` — the Z-axis rotation in radians.

<br/>

### lookAt

> `CFrame`
>
> `CFrame.lookAt(position: Vector3, target: Vector3)`
>
> Creates a CFrame at `position` oriented toward `target`.

#### Parameters

- `position`: `Vector3` — the position of the CFrame.
- `target`: `Vector3` — the point toward which the CFrame faces.

<br/>

## Methods

### GetComponents

> `...Number`
>
> `cframe:GetComponents()`
>
> Returns the position and rotation-matrix components of the CFrame.

<br/>

### Inverse

> `CFrame`
>
> `cframe:Inverse()`
>
> Returns the inverse transformation of `cframe`.

<br/>

### Lerp

> `CFrame`
>
> `cframe:Lerp(goal: CFrame, alpha: Number)`
>
> Interpolates between `cframe` and `goal`.

#### Parameters

- `goal`: `CFrame` — the target transformation.
- `alpha`: `Number` — the interpolation amount, from `0` to `1`.

<br/>

### PointToObjectSpace

> `Vector3`
>
> `cframe:PointToObjectSpace(point: Vector3)`
>
> Converts a world-space point to the CFrame's object space.

#### Parameters

- `point`: `Vector3` — the world-space point.

<br/>

### PointToWorldSpace

> `Vector3`
>
> `cframe:PointToWorldSpace(point: Vector3)`
>
> Converts an object-space point to world space.

#### Parameters

- `point`: `Vector3` — the object-space point.

<br/>

### ToEulerAnglesXYZ

> `Number, Number, Number`
>
> `cframe:ToEulerAnglesXYZ()`
>
> Returns the CFrame rotation as X, Y, and Z Euler angles in radians.

<br/>

### ToEulerAnglesYXZ

> `Number, Number, Number`
>
> `cframe:ToEulerAnglesYXZ()`
>
> Returns the CFrame rotation as X, Y, and Z Euler angles in radians, using YXZ order.

<br/>

### ToObjectSpace

> `CFrame`
>
> `cframe:ToObjectSpace(other: CFrame)`
>
> Converts `other` into `cframe`'s object space.

#### Parameters

- `other`: `CFrame` — the world-space transformation.

<br/>

### ToOrientation

> `Number, Number, Number`
>
> `cframe:ToOrientation()`
>
> Returns the CFrame rotation as X, Y, and Z orientation angles in radians.

<br/>

### ToWorldSpace

> `CFrame`
>
> `cframe:ToWorldSpace(other: CFrame)`
>
> Converts `other` from `cframe`'s object space to world space.

#### Parameters

- `other`: `CFrame` — the object-space transformation.

<br/>

### VectorToObjectSpace

> `Vector3`
>
> `cframe:VectorToObjectSpace(vector: Vector3)`
>
> Converts a world-space direction vector to object space without applying position.

#### Parameters

- `vector`: `Vector3` — the world-space direction vector.

<br/>

### VectorToWorldSpace

> `Vector3`
>
> `cframe:VectorToWorldSpace(vector: Vector3)`
>
> Converts an object-space direction vector to world space without applying position.

#### Parameters

- `vector`: `Vector3` — the object-space direction vector.

<br/>

## Position and rotation example

A CFrame stores position and rotation together. Angles use radians, so `math.rad` makes degree values easier to read:

```luau
local position = CFrame.new(0, 5, 0)
local quarterTurn = CFrame.Angles(0, math.rad(90), 0)
local transform = position * quarterTurn

local part = workspace:FindFirstChild("MyPart")
if part then
    part.CFrame = transform
end
```

Multiplication composes transforms. In this example, the Part is placed five studs above the origin and rotated 90 degrees around the Y axis.

## Operators

The following expressions completed successfully in both `Script` and `LocalScript`:

```lua
cframe + vector3
cframe - vector3
cframe * otherCFrame
cframe * vector3
```

Addition and subtraction translate the CFrame. Multiplication composes two CFrames or transforms a `Vector3` point.

## Testing Notes

These observations were revalidated in both Script and LocalScript in Vortex Studio 0.3.4.

`CFrame.fromMatrix` requires all three basis vectors. Calling it without `vZ` fails because the current implementation indexes the missing argument.

The lowercase aliases `components`, `toEulerAnglesXYZ`, and `toEulerAnglesYXZ` are also exposed; this reference uses the canonical names.

The position-and-rotation example was revalidated in Vortex Studio 0.3.8. It produced position `(0, 5, 0)` and a LookVector of approximately `(-1, 0, 0)`.
