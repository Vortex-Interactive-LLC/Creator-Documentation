---
title: Tags
description: Tags are labels you put on instances so a script can find all of them at once.
---
> [!Summary]
> A tag is a string label on an Instance. Tag many objects with the same tag, then use `CollectionService:GetTagged` to get all of them in one call.

### Adding tags

In Studio, select an instance and type a name into **Add Tag** in the Properties panel, then press Enter. With several instances selected, the section lists the tags they all share, and adding or removing a tag applies to all of them. Tag changes can be undone.

In a script:

```luau
part:AddTag("Door")
print(part:HasTag("Door")) --> true
print(part:GetTags()) --> { "Door" }
part:RemoveTag("Door")
```

A tag is 1 to 255 bytes with no control characters, and tags are case sensitive. An Instance can have at most 100 tags.

### Finding tagged instances

```luau
local CollectionService = game:GetService("CollectionService")

local function setup(door)
    door.Touched:Connect(function()
        print(door.Name, "touched")
    end)
end

for _, door in CollectionService:GetTagged("Door") do
    setup(door)
end
CollectionService:GetInstanceAddedSignal("Door"):Connect(setup)
```

`GetTagged` only returns instances that are in the game. `GetInstanceAddedSignal` handles doors that appear later, such as a tagged model cloned in at runtime.

### Saving and replication

Tags are saved with the place. Tags added on the server replicate to clients, so a `LocalScript` can call `GetTagged` as well. Tags added on a client are local to that client.

See [CollectionService](../reference/classes/collection-service.md) and [Instance](../reference/classes/instance.md).
