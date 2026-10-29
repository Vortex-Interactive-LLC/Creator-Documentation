---
title: ReplicatedStorage
description: Contains instances that are loaded by both the server and the client.
---

## Summary

ReplicatedStorage is a container for items that should be visible to both the
server and the client. Items placed here will automatically have their
properties synchronized from the server.

<details>
<summary><b>Properties</b></summary>
Properties of `ReplicatedStorage`.
<br><br>

- [ClassName](#classname): `string`
- [Name](#name): `string`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `ReplicatedStorage`.
<br><br>

- [FindFirstChild](#findfirstchild): [`Instance`](./instance.md) | `nil`
- [GetChildren](#getchildren): `{ Instance }`
- [WaitForChild](#waitforchild): [`Instance`](./instance.md)

</details>

## Parenting

Place a `Part` in `ReplicatedStorage` by setting its `Parent` to `ReplicatedStorage`:

```luau
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local part = Instance.new("Part")
part.Name = "SharedPart"
part.Parent = ReplicatedStorage
```

## Properties

### ClassName
> `string` \
\
The runtime class name of the service.

<br/>


### Name
> `string` \
\
The service name shown by the runtime.

<br/>

## Methods

### FindFirstChild()
> [`Instance`](./instance.md) | `nil` \
\
`ReplicatedStorage:FindFirstChild(name: string)` \
\
Returns the first direct child with the supplied `name`, or `nil` when none is
found.

#### Parameters

- `name`: `string` — the name of the child to find.

<br/>


### GetChildren()
> `{ Instance }` \
\
Returns the direct children of `ReplicatedStorage`.

<br/>


### WaitForChild()
> [`Instance`](./instance.md) \
\
`ReplicatedStorage:WaitForChild(name: string)` \
\
Waits for and returns a direct child with the supplied `name`.

#### Parameters

- `name`: `string` — the name of the child to wait for.

<br/>


## Testing Notes

These observations are from Vortex Studio 0.3.4 and may differ in later
releases.

A temporary `Part` can have its `Parent` set to `ReplicatedStorage`, and
`WaitForChild` resolves it. `FindFirstChild` returns `nil` and `GetChildren`
omits it.
