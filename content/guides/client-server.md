---
title: Client and Server
description: Explains the client and server
---
> [!Summary]
> Vortex games run on a client-server model where the server owns the authoritative game state. The client handles local input, visuals, and UI, while the server validates and applies world changes.

Vortex games operate with a client-server model.
- Server: The server is the authoritative side that runs the actual game and is the source of the game's state.
- Client: A client is the player’s instance of the game running on their device.

## Server
The server is the authoritative side of the game. It runs separately from the player’s device and is responsible for managing the actual state of the game, such as player data, game rules, damage, currency, and other state that needs to be trusted and synchronized between players.

Server-side code runs in [Scripts](../reference/classes/script.md).

## Client
The client is the player’s side of the game. It runs on the player’s device and is responsible for things that the player directly sees and interacts with, such as rendering the world, displaying UI, playing animations, and receiving input from the player.

Client-side code runs in [LocalScripts](../reference/classes/localscript.md).

---

Whenever handling `Client → Server` remotes, make sure to properly validate the data sent by the client. A good rule of thumb is to let the client signal intent, but do not let it make authoritative decisions about game state. E.g.:
  - Bad: Player clicks a buy button. On their client, they subtract their own money, give themselves the item, then inform the server of the transaction that occurred.
  - Good: Player clicks a buy button. The client informs the server of its intent. The server validates whether the player has enough money and, if they do, changes their money and gives them the item.

## Identifying the player

When a client fires a [`RemoteEvent`](../reference/classes/remote-event.md), the server's `OnServerEvent` handler receives that client's `Player` as its first argument. Use it to target the caller, for example `player.Character`. Remote arguments cannot be Instances, so send names, ids, or other primitive values instead.
