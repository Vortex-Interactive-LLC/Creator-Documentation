---
title: ProximityPrompt
description: Shows an interaction prompt near its parent when a player is close.
---

## Summary

A `ProximityPrompt` inside a `Part` or an `Attachment` shows a prompt to nearby players. The player presses a key (optionally holding it) to trigger it, and scripts react to [`Triggered`](#signals). Prompts only work while the parent is in the `Workspace`.

### Example

```luau
local prompt = Instance.new("ProximityPrompt")
prompt.ActionText = "Open"
prompt.ObjectText = "Door"
prompt.HoldDuration = 0.5
prompt.Parent = workspace.Door

prompt.Triggered:Connect(function(player)
    print(player.Name, "opened the door")
end)
```

## Properties

- `ActionText` - `string`, what pressing the key does. Defaults to `"Interact"`;
- `ObjectText` - `string`, the name of the thing being interacted with. Defaults to empty;
- `Enabled` - `boolean`, whether the prompt can be shown and triggered. Defaults to `true`;
- `HoldDuration` - `number`, seconds the key must be held before `Triggered` fires. `0` triggers on press. Defaults to `0`;
- `KeyboardKeyCode` - [`Enum.KeyCode`](../globals/enum.md), the key that triggers the prompt. Defaults to `E`;
- `MaxActivationDistance` - `number`, how close in studs the player's character must be. Defaults to `10`;
- `RequiresLineOfSight` - `boolean`, hides the prompt when something solid is between the camera and the prompt. Defaults to `true`;
- `Exclusivity` - `Enum.ProximityPromptExclusivity`, how prompts that share a key are shown. `OnePerButton` shows only the nearest prompt per key, `OneGlobally` shows only the nearest prompt overall, `AlwaysShow` always shows it. Defaults to `OnePerButton`;
- `Style` - `Enum.ProximityPromptStyle`, `Default` draws the built-in prompt and `Custom` draws nothing so your own UI can use `PromptShown` and `PromptHidden`. Defaults to `Default`;
- `UIOffset` - `Vector2`, a pixel offset for the built-in prompt;
- `Name` - the name of the instance;
- `ClassName` - `"ProximityPrompt"`;
- `Parent` - the `Part` or `Attachment` it belongs to.

## Signals

- `Triggered` - passes the [`Player`](./player.md) who completed the press or hold;
- `TriggerEnded` - passes the `Player` who released the key after triggering;
- `PromptButtonHoldBegan` - passes the `Player` who started holding the key, when `HoldDuration` is above `0`;
- `PromptButtonHoldEnded` - passes the `Player` who released or lost the prompt before or after the hold finished, when `HoldDuration` is above `0`;
- `PromptShown` - fires in a `LocalScript` when the prompt becomes available to the local player;
- `PromptHidden` - fires in a `LocalScript` when it stops being available.

The first four signals fire on both the server and the owning client. A server `Script` only sees a trigger when the server agrees the player's character is within `MaxActivationDistance` plus a small allowance.
