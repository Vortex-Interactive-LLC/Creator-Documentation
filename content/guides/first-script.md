---
title: Your First Script
description: Learn how to make your first script in Vortex Studio.
---

<!-- 
Your first script
Revision 2

Written by Kindtracker on August 29th, 2026
-->

Let's make a Hello World script. Create a script in ServerScriptService. You will see:
```lua
print("Hello, world!")
```
Then playtest the game. You will see "Hello, world!" in the output. Now, let's spawn a part in Workspace.

```lua
local part = Instance.new("Part")
```
We need to put it in Workspace.
```lua
part.Parent = workspace
```
We made a part! Let’s change its position, size, name, and color!
```lua
part.Name = "MyPart"
part.Size = Vector3.new(2, 2, 2)
part.Position = Vector3.new(0, 10, 0)
part.Color = Color3.fromRGB(192, 32, 12)
part.Anchored = false
```
Playtest your game and you will see a red part named "MyPart" with a size of `2, 2, 2` and Anchored property set to false.

[`workspace`](../reference/classes/workspace.md) is a built-in shortcut for the Workspace service. However, other services don't have built-in shortcuts, so you need to use `game:GetService(serviceName: string)` to access them.

