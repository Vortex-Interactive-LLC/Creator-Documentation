---
title: StarterPlayerScripts
description: A container inside the "StarterPlayer" service that stores client-side scripts.
---

# What is StarterPlayerScripts?

**StarterPlayerScripts** is a container inside the `StarterPlayer` service that stores client-side scripts. These scripts are automatically copied to a player's `PlayerScripts` container when the player joins the game.
> [!CAUTION]
> Do not confuse `StarterPlayerScripts` with `StarterCharacterScripts`. Although they are similar, they serve different purposes.

It is commonly used for scripts that control player-specific behavior and other systems that run on the player's device.

# What is StarterPlayerScripts used for?

`StarterPlayerScripts` is commonly used for:

- Client-side game systems
- Player input handling
- Camera systems
- Client-side effects and animations
- User interface logic
- Keyboard, mouse, and controller input
- Local player movement systems
- Client-side visual effects

# How does StarterPlayerScripts work?

Scripts placed inside `StarterPlayerScripts` are automatically copied into the player's `PlayerScripts` container when the player joins the experience.

`StarterPlayerScripts` is primarily intended for `LocalScripts`, which run on the client.

> [!NOTE]
> Do not place a server `Script` inside `StarterPlayerScripts` and expect it to run on the server. Server scripts do not execute there. `ModuleScripts` can be used for client-side modules when they are required by scripts running on the client. For modules that need to be accessible to both the client and the server, consider placing them in `ReplicatedStorage`.

# Security Considerations

Do **not** use `StarterPlayerScripts` for server-side security or validation.

Client-side code should never be trusted to enforce security-sensitive logic because it runs on a device controlled by the player.

> [!CAUTION]
> Never rely on `StarterPlayerScripts` for server validation, anti-cheat enforcement, or other security-critical logic. All important validation should be performed on the server.
