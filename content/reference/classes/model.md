---
title: Model
description: A collection of Explorer items grouped into one object.
---

<!-- 
Model
Revision 1

Written by KingTasaz on August 28th, 2026
-->

## Summary
Models are a very simple way to group [`parts`](./part.md) together. Creating a model requires at least `2` selected parts, but the second part can be deleted afterward. Parts in a model are not truly connected; they are only grouped in the Explorer. Models currently have no purpose other than organization.

A model with no children is still shown in the explorer, but does not exist in the world and has no transform controls.

The basic transform tools (Move, Rotate) work more or less as expected when used on a model, except for scaling, which is currently not properly supported.

<details>
<summary><b>Properties</b></summary>
Properties of a Model, in the order they appear in Vortex Studio
<br><br>
<ul>

<details>
<summary><b>Properties</b></summary>

- [Name](#name): `string`
- [Position](#position): [`Vector3`](../datatypes/vector3.md)

</details>

</ul>
</details>

## Properties


### Name
> `string` \
\
The name of the `model` and its label in the Explorer.

<br/>


### Position
> [`Vector3`](../datatypes/vector3.md) \
\
The position of the `model`, in world space. A model's position is automatically set to the mathematical average of the positions of all its children. (See [Images](#images))

<br/>

## Images
<img src="../../../images/examples/modelCenterExample1.png" alt="Model w/ Move Tool" width="400"/>

## Notes

A `Model` exposes the generic instance surface, including hierarchy and attribute methods. Instances parented to a Model become its children: `FindFirstChild`, `GetChildren()`, `GetDescendants()`, and `WaitForChild` all find them. `GetPivot`, `PivotTo`, and `MoveTo` are available. `Position`, `PrimaryPart`, and `WorldPivot` are not readable from a script, and `GetPrimaryPartCFrame` and `SetPrimaryPartCFrame` are not available.

The live [Character](./character.md) Model is a special case. It exposes `ClassName`, `Name`, and `Position`, plus direct `Humanoid` and `HumanoidRootPart` members; `Parent` reads as `nil`. It provides the generic Instance methods, `MoveTo`, and `PivotTo`.

The live Character Model is also the target for write-only visual rotation: `character.Orientation = Vector3.new(0, 90, 0)` turns the character while the field remains `nil` on readback. See [Character: Write-only visual rotation](./character.md#write-only-visual-rotation).

`Character:FindFirstChild("Humanoid")` and `Character:FindFirstChild("HumanoidRootPart")` return the same direct members. The standard R6/R15 body parts are not children of the character. Character attribute values replicate in both directions between a server Script and the owning LocalScript; see the [Attributes guide](../../guides/attributes.md).

## Transient Character visual Scene

The unnamed child returned by `Character:GetChildren()` can expose a `Scene` member after the visual character finishes loading. This is a separate, transient render hierarchy; it is not part of the stable public Character projection above. Code that needs it must poll until the path is available and re-resolve it after every replacement:

```luau
local function getCharacterScene(character)
    for _, wrapper in ipairs(character:GetChildren()) do
        local ok, scene = pcall(function() return wrapper.Scene end)
        if ok and scene then
            return scene
        end
    end
end
```

After the Scene resolves, its primary rig path is also directly indexable:

```luau
local armature = scene["Armature.001"]
local visualRoot = armature.HumanoidRootPart
local torso = visualRoot.Torso
local leftArm = torso["Left Arm"]
```

The bracket form is required for the dot-containing `Armature.001` name and for limb names containing spaces. This inner visual root is distinct from the public `Character.HumanoidRootPart` Part projection.

The following is the observed character projection after the visual Scene and the test avatar's attachments finished loading. `Humanoid` and the outer `HumanoidRootPart` are the stable direct Character members; the tree below the anonymous wrapper is the transient visual projection:

```text
Character (Model)
├── Humanoid                              public direct member
├── HumanoidRootPart (Part projection)    public direct member
└── <unnamed wrapper>                      Character:GetChildren()[1]
    └── Scene
        ├── Armature.001
        │   └── HumanoidRootPart           visual generic Instance
        │       └── Torso
        │           ├── Right Arm
        │           ├── Left Arm
        │           ├── Right Leg
        │           ├── Left Leg
        │           ├── <unnamed attachment>
        │           │   └── Scene
        │           │       └── Spike Sword
        │           │           └── Spike Sword.FBXASC051SG
        │           ├── <unnamed attachment>
        │           │   └── Scene
        │           │       └── Angel wings
        │           │           └── Angel wings.initialShadingGroup.002
        │           ├── <unnamed attachment>
        │           │   └── Scene
        │           │       └── Body.003
        │           │           └── R7Body.028.Material.034
        │           └── Head
        │               ├── <unnamed attachment>
        │               │   └── Scene
        │               │       └── PaperPlane Hat
        │               │           └── PaperPlane Hat.initialShadingGroup.011
        │               └── <unnamed attachment>
        │                   └── Scene
        │                       └── 3.002
        │                           └── 3.002.Hair
        └── Body
            └── R7Body.Material.*          six observed render-material nodes
```

The named accessory and material leaves come from a specific test-avatar capture and are not guaranteed to appear in every hierarchy. The repeated unnamed attachment nodes are the stable structural pattern: they are direct children of `Torso` or `Head`, and their nested `Scene` contains the rendered attachment content.

All of these visual nodes report `ClassName == "Instance"`. The observed surface is the generic hierarchy and attribute method set, plus readable `Name`, `Parent`, `Position`, and `Size`. `Changed`, `Touched`, and `TouchEnded` can be connected, but no delivery was observed when a limb's `Position` changed. The live limb transforms are therefore readable render state, not a replacement for the public `HumanoidRootPart` projection.

Visual rig and attachment nodes also accept numeric `Transparency` writes in both a LocalScript and a server Script. An initially unset value reads as `nil`; after `node.Transparency = 0.5` or `0`, it reads back as that numeric value. The tested torso and leg did not visibly change when the field was written, so this is currently stored projection state rather than a confirmed render-opacity control. In contrast, the public [`Character.HumanoidRootPart`](./humanoid-root-part.md) rejects the same write in both contexts.

The hierarchy changes during loading. In one verified run, unnamed attachment nodes appeared below `Torso` and `Head`, and each then exposed a nested `Scene`. Their visual content included `Angel wings`, `Spike Sword`, hair, and a `PaperPlane Hat`. Those names are avatar-specific examples, not guaranteed children. Later, Vortex replaced the entire `Scene` and `Armature.001` with a fresh base hierarchy; a direct `Cube` node also appeared on the replacement Scene in the observed run. Do not retain visual-node references across frames or loading phases; reacquire `Scene`, `Armature.001`, and any limb or attachment from the current Character hierarchy.

A replacement destroys the old visual nodes rather than simply detaching them. After a replacement, trying to reparent a stored accessory node into the new visual rig failed with `Instance no longer exists`. A script can restore a node that was manually reparented during its current Scene generation, but it cannot carry that node across Vortex's Scene rebuild.

Reparenting `Right Arm` and `Left Arm` from this visual hierarchy was observed to hide the corresponding rendered arms in both a LocalScript and a server Script. This is an implementation detail rather than a stable character API; test it against the target avatar and expect visual Scene replacements to undo the change.
