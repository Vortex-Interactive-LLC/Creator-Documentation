---
title: CollectionService
description: A service that finds instances by their tags
---

## Summary

<details>
<summary><b>Methods</b></summary>

Methods available on `CollectionService`.
<br><br>

* [GetTagged](#gettagged)
* [GetAllTags](#getalltags)
* [GetInstanceAddedSignal](#getinstanceaddedsignal)
* [GetInstanceRemovedSignal](#getinstanceremovedsignal)

</details>

## Overview

`CollectionService` finds every instance that has a given tag. Tags are added in Studio or with [`Instance:AddTag`](./instance.md#addtagtag-string), so one script can control many objects without looping over the whole game.

```lua
local CollectionService = game:GetService("CollectionService")

for _, door in CollectionService:GetTagged("Door") do
    door.Transparency = 0.5
end
```

## Methods

### GetTagged

> `CollectionService:GetTagged(tag: string): { Instance }`
>
> Returns every instance that has `tag` and is in the game. An instance that is not a descendant of the game, such as one with no parent, is not returned.

#### Parameters

- `tag`: `string` - the tag to look for.

<br/>

### GetAllTags

> `CollectionService:GetAllTags(): { string }`
>
> Returns every tag that at least one instance in the game has.

<br/>

### GetInstanceAddedSignal

> `CollectionService:GetInstanceAddedSignal(tag: string): Signal`
>
> Returns a signal that fires with the instance when an instance with `tag` enters the game. This happens when the tag is added to an instance already in the game, or when a tagged instance is parented into the game.

#### Parameters

- `tag`: `string` - the tag to watch.

<br/>

### GetInstanceRemovedSignal

> `CollectionService:GetInstanceRemovedSignal(tag: string): Signal`
>
> Returns a signal that fires with the instance when an instance with `tag` leaves the game. This happens when the tag is removed, the instance is parented out of the game, or it is destroyed.

#### Parameters

- `tag`: `string` - the tag to watch.

## Notes

The signals do not fire for instances that were already tagged when you connected. Combine `GetTagged` with the added signal to handle both:

```lua
local function setup(door)
    door.Transparency = 0.5
end

for _, door in CollectionService:GetTagged("Door") do
    setup(door)
end
CollectionService:GetInstanceAddedSignal("Door"):Connect(setup)
```

Tags set on the server replicate to clients, so a `LocalScript` can use `GetTagged` too. Tags added on a client stay on that client. If the server later changes the same instance's tags, the client's tags for that instance are replaced by the server's.
