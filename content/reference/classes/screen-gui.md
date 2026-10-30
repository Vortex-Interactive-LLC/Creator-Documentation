---
title: ScreenGui
description: The root of an on-screen interface.
---

## Summary

A `ScreenGui` holds GUI objects that are drawn over the game. Place one in `StarterGui` and each player receives a copy in their [`PlayerGui`](./player-gui.md). See [Building GUIs](../../guides/gui.md).

## Properties

- `Enabled` - `boolean`, defaults to `true`. When `false` nothing inside it is drawn;
- `DisplayOrder` - `number`, higher values are drawn on top and receive input first. Defaults to `0`;
- `ResetOnSpawn` - `boolean`, defaults to `true`. When `true` the player's copy is replaced with a fresh one from `StarterGui` each time their character respawns;
- `Name`, `ClassName`, `Parent`.
