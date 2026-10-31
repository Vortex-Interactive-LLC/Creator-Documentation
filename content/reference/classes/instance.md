---
title: Instance
description: The methods and properties shared by objects in the game.
---

> [!IMPORTANT]
> Most instances share the members below. A few engine-backed values do not: `Humanoid` exposes none of the generic Instance methods, `HumanoidRootPart` exposes only `IsA`, and `Players` exposes only `FindFirstChild` and `GetChildren`. Check the availability matrix at the end of this page and the concrete class reference before calling a method.

## Properties

- `Name` - `string`, the name of the instance;
- `ClassName` - `string`, the class of the instance;
- `Parent` - `Instance | nil`, its parent in the hierarchy, or `nil` when it has none.

## Methods

### Clone()

> `Instance`
>
> Creates and returns a copy of the instance. The cloned instance contains the same properties and child objects as the original instance.
>
> ```luau
> local clone = part:Clone()
> clone.Parent = workspace
> ```
>
> The original instance is not modified when a clone is created.

### Destroy()

> `nil`
>
> Removes the Instance and its descendants from the game. Once an instance is destroyed, it can no longer be used normally.
>
> ```luau
> part:Destroy()
> ```
>
> `Destroy()` also disconnects connections associated with the instance and removes it from its parent.

### FindFirstChild(name: `string`)

> `Instance?`
>
> Searches for a child of the Instance with the specified name and returns it if one is found.
>
> ```luau
> local part = workspace:FindFirstChild("Part")
> ```
>
> If no child with the specified name is found, the method returns `nil`.

### FindFirstChildOfClass(className: `string`)

> `Instance?`
>
> Returns the first direct child whose class is `className`, or `nil` if there is none.
>
> ```luau
> local model = workspace:FindFirstChildOfClass("Model")
> local humanoid = character:FindFirstChildOfClass("Humanoid")
> ```
>
> Only direct children are searched.

### GetChildren()

> `Array`
>
> Returns an array containing all direct children of the Instance.
>
> ```luau
> local children = workspace:GetChildren()
> ```
>
> Only direct children are returned. Objects nested inside other children are not included.

### GetDescendants()

> `Array`
>
> Returns an array of all the Instance's descendants: its children, their children, and so on.
>
> ```luau
> for _, descendant in model:GetDescendants() do
>     if descendant:IsA("BasePart") then
>         descendant.Anchored = true
>     end
> end
> ```

### WaitForChild(name: `string`, timeout: `Number?`)

> `Instance?`
>
> Waits for a child with the specified name to exist, then returns that child.
>
> If the child already exists, it is returned immediately. If the child does not exist, the function waits until it becomes available.
>
> An optional `timeout` can be provided to limit how long the function waits. If the timeout expires before the child is found, `nil` is returned.
>
> ```luau
> local part = workspace:WaitForChild("Part")
> print(part.Name)
> ```
>
> With a timeout:
>
> ```luau
> local part = workspace:WaitForChild("Part", 5)
>
> if part then
>     print("Part found")
> end
> ```

### IsA(className: `string`)

> `boolean`
>
> Returns `true` if the Instance is of the class `className` or inherits from it.
>
> ```luau
> print(part:IsA("Part"))     --> true
> print(part:IsA("BasePart")) --> true
> print(part:IsA("Instance")) --> true
> print(part:IsA("Model"))    --> false
> ```

### GetAttribute(name: `string`)

> `boolean | number | string | nil`
>
> Returns the value of the attribute `name`, or `nil` if the attribute is not set.
>
> ```luau
> part:SetAttribute("Health", 5)
> print(part:GetAttribute("Health")) --> 5
> print(part:GetAttribute("Missing")) --> nil
> ```
>
> See [Attributes](../../guides/attributes.md).

### GetAttributes()

> `{ [string]: boolean | number | string }`
>
> Returns a table of every attribute on the Instance, keyed by name.
>
> ```luau
> for name, value in part:GetAttributes() do
>     print(name, value)
> end
> ```

### SetAttribute(name: `string`, value: `boolean | number | string | nil`)

> `nil`
>
> Sets the attribute `name` to `value`. Passing `nil` removes the attribute.
>
> ```luau
> part:SetAttribute("Health", 5)
> part:SetAttribute("Health", nil)
> ```
>
> Attributes can only hold booleans, numbers, strings, or `nil`. Any other value, such as a `Vector3`, raises an error, as does an empty name.

### GetAttributeChangedSignal(name: `string`)

> [`Signal`](../datatypes/signal.md)
>
> Returns a signal that fires when the attribute `name` changes.
>
> ```luau
> part:GetAttributeChangedSignal("Health"):Connect(function()
>     print("Health is now", part:GetAttribute("Health"))
> end)
> ```
>
> The signal fires when the attribute changes, whether or not the Instance has a parent yet.

### GetPropertyChangedSignal(property: `string`)

> [`Signal`](../datatypes/signal.md)
>
> Returns a signal that fires after the property `property` changes.
>
> ```luau
> part:GetPropertyChangedSignal("Transparency"):Connect(function()
>     print("Transparency is now", part.Transparency)
> end)
> ```
>
> The signal fires when the property changes, whether or not the Instance has a parent yet. A property name that does not exist does not raise an error, but its signal never fires.

### GetPivot()

> [`CFrame`](../datatypes/cframe.md)
>
> Returns the pivot of the Instance. For a `Part` this is its `CFrame`. For a `Model` it is the centre of the model's parts.
>
> ```luau
> local pivot = model:GetPivot()
> print(pivot.Position)
> ```

### PivotTo(targetCFrame: [`CFrame`](../datatypes/cframe.md))

> `nil`
>
> Moves the Instance so that its pivot is at `targetCFrame`. On a `Model`, every part moves with it and keeps its position relative to the pivot.
>
> ```luau
> model:PivotTo(CFrame.new(0, 20, 0))
> ```
>
> It can also be called on a `Part` and on a player's character. On a character, only the rotation around the Y axis is used. See [`GetPivot`](#getpivot).

### MoveTo(position: [`Vector3`](../datatypes/vector3.md))

> `nil`
>
> Moves a `Model` so that its pivot is at `position`.
>
> ```luau
> model:MoveTo(Vector3.new(10, 30, 10))
> ```
>
> `MoveTo` is only available on models and characters. Calling it on a `Part` raises an error, so set the part's `Position` or use [`PivotTo`](#pivottotargetcframe-cframe).

## Vortex Studio Method Availability

The following matrix records whether each member is exposed as a function on the live object.

| Runtime object | `FindFirstChild` | `FindFirstChildOfClass` | `WaitForChild` | `GetChildren` | `GetDescendants` | `Clone` | `Destroy` | `IsA` |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [`Part`](./part.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Script`](./script.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Character`](./character.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Workspace`](./workspace.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`ReplicatedStorage`](./replicated-storage.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`ServerScriptService`](./server-script-service.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Player`](./player.md) | Yes | Yes | Yes | Yes | Yes | Yes | Yes | Yes |
| [`Players`](./players.md) | Yes | No | No | Yes | No | No | No | No |
| [`Humanoid`](./humanoid.md) | No | No | No | No | No | No | No | No |
| [`HumanoidRootPart`](./humanoid-root-part.md) | No | No | No | No | No | No | No | Yes |

`Players` also provides its class-specific methods such as `GetPlayers()`, and a `Humanoid` provides `IsDead()`, `GetState()`, and `TakeDamage()`, even though the generic methods above are absent.
