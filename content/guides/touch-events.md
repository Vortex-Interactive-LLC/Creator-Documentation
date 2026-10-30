---
title: Touch Events
description: Detect parts touching each other and players with Touched and TouchEnded.
---
A `Part` has two touch events: `Touched` fires when another part starts touching it, and `TouchEnded` fires when that contact stops. Both pass the part that touched it.

```luau
-- Script
local Players = game:GetService("Players")
local pad = workspace.Pad

pad.Touched:Connect(function(hit)
    local player = Players:GetPlayerFromCharacter(hit.Parent)
    if player then
        print(player.Name, "stepped on the pad")
    end
end)

pad.TouchEnded:Connect(function(hit)
    local player = Players:GetPlayerFromCharacter(hit.Parent)
    if player then
        print(player.Name, "stepped off the pad")
    end
end)
```

## What touches what

When a player touches a part, `hit` is one of the character's body parts. `hit.Parent` is the character, so `Players:GetPlayerFromCharacter(hit.Parent)` returns the player, and `hit.Parent:FindFirstChildOfClass("Humanoid")` returns their `Humanoid`.

`Touched` fires when contact begins, not every frame. A player standing still on a pad does not fire it again. Walking off fires `TouchEnded`, and walking back on fires `Touched` again.

Parts with `CanCollide` off still fire touch events, which makes them good invisible trigger zones. Parts that are not inside the `Workspace` do not.

## Connecting

You can connect before or after a part is parented into the `Workspace`, and parts created with `Instance.new` fire normally.

```luau
local trigger = Instance.new("Part")
trigger.Anchored = true
trigger.Size = Vector3.new(6, 1, 6)
trigger.Position = Vector3.new(0, 0.5, 0)
trigger.Touched:Connect(function() print("touched") end)
trigger.Parent = workspace
```

If `CanTouch` is `false`, connecting to `Touched` or `TouchEnded` raises an error. Setting `CanTouch` to `false` later disconnects the connections already made, and you need to connect again after turning it back on. Destroying a part disconnects its connections.

`Signal:Once` and `Signal:Wait` also work with these events. See [Events](events.md).
