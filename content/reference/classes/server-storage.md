---
title: ServerStorage
description: Holds instances that only the server can see.
---

## Summary

`ServerStorage` is a container for items that only the server needs. Nothing inside it is sent to players, so it is a safe place for assets, such as a template to clone, that you do not want players to see. Get it with `game:GetService("ServerStorage")` in a server `Script`.

```luau
local ServerStorage = game:GetService("ServerStorage")

local template = ServerStorage:WaitForChild("Enemy")
local enemy = template:Clone()
enemy.Parent = workspace
```

## Properties

- `Name`, `ClassName`.
