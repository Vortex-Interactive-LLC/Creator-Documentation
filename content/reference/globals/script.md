---
title: script
description: The script that is currently running.
---

`script` is the instance of the script that is running, so you can read its `Parent` and the instances near it.

```luau
print(script.Name, script.Parent)
```

Inside a `ModuleScript`, `script` is the script that called `require`, not the module. Use an explicit path such as `game.ReplicatedStorage.Helper` to find other modules.
