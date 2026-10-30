---
title: StarterGui
description: A service holding the GUIs given to every player.
---

## Summary

Get the service with `game:GetService("StarterGui")`. Place a [`ScreenGui`](./screen-gui.md) inside it, and every player receives a copy in their [`PlayerGui`](./player-gui.md) when they join. See [Building GUIs](../../guides/gui.md).

Changing a `ScreenGui` in `StarterGui` does not change the copies players already have.
