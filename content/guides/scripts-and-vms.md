---
title: Scripts and VMs
description: Learn how scripts execute Luau code and interact with the Vortex engine at runtime.
---

> [!Summary]
> Scripts hold Luau source code that the engine executes through the Luau virtual machine. The VM compiles script code into bytecode, runs it at runtime, and lets it interact with the game through engine APIs.

### Scripts

> A script is a container that holds Luau source code. Scripts are used to define gameplay logic and interact with the engine.

> Here's a simple example:

```lua
local part = Instance.new("Part")
part.Parent = game.Workspace
```

> [!NOTE]
> Although this example only creates an instance and assigns its parent, scripts can be used to implement significantly more complex gameplay systems and engine interactions.

> The source code stored within a script is not executed directly by the script container. Instead, the engine passes the source code to the Luau runtime, where it is compiled and executed by the Luau Virtual Machine (VM).

> The currently supported script types are:

* `LocalScript`
* `Script`

### Luau Virtual Machine

> The Luau Virtual Machine (VM) is responsible for executing compiled Luau code at runtime.

> When a script is executed, the engine retrieves the source code stored within the script and passes it to the Luau runtime. The Luau compiler then processes the source code and produces bytecode, which is executed by the Luau VM.

> The VM manages the execution state of the running code, including values, function calls, control flow, and other runtime operations.

> A simplified representation of the execution pipeline is:

> **Script → Luau Source Code → Luau Compiler → Bytecode → Luau VM → Engine APIs → Game**

> The **Script** stores the source code, while the **Luau compiler** converts that source code into bytecode. The **Luau VM** executes the resulting bytecode, while **engine APIs** provide the functionality required for Luau code to interact with the game and engine systems.

### Engine Integration

> Vortex uses **Bevy** as its underlying engine layer.

> Vortex exposes engine functionality to Luau through its scripting APIs, allowing scripts to interact with game objects and other engine systems.
