---
title: Players
description: A container that holds all players currently connected as Player objects.
---

## Summary

<details>
<summary><b>Properties</b></summary>
Properties of `Players`.
<br><br>

* [LocalPlayer](#localplayer): `Player?`

</details>

<details>
<summary><b>Methods</b></summary>
Methods of `Players`.
<br><br>

* [GetPlayers](#getplayers): `{Player}`
* [GetPlayerByUserId](#getplayerbyuserid): `Player?`
* [GetPlayerFromCharacter](#getplayerfromcharacter): `Player?`

</details>

<details>
<summary><b>Signals</b></summary>
Signals of `Players`.
<br><br>

* [PlayerAdded](#playeradded): `Connection`
* [PlayerRemoving](#playerremoving): `Connection`

</details>

## Overview

A service representing connected clients as
[Player](./player.md) instances.

### Example

```luau
-- LocalScript

local Players = game:GetService("Players")

local everyPlayer = Players:GetPlayers()
local player = Players.LocalPlayer
```

## Properties

### LocalPlayer

> `Players.LocalPlayer: Player?`
>
> Refers to the `Player` whose client is running the experience. Available only in a `LocalScript`; otherwise, it will return `nil`.

## Methods

### GetPlayers

> `GetPlayers(): {Player}`
>
> Returns the currently visible player list.

### GetPlayerByUserId

> `GetPlayerByUserId(UserId: number): Player`
>
> Returns the `Player` with the specified `UserId`. **Only if this player is on the server.**

#### Parameters

- `UserId: number` — `UserId` of the player being specified.

### GetPlayerFromCharacter

> `GetPlayerFromCharacter(Character: Model): Player`
>
> Returns the player associated with the specified character. 

#### Parameters

- `Character: Model` — A character instance that you want to get the player from.

## Signals

### PlayerAdded

> `PlayerAdded(player: Player): Connection`
>
> Fires when a player joins the server. Returns `Connection`.

#### Parameters

- `player: Player` — a player who has joined the server.

### PlayerRemoving

> `PlayerRemoving(player: Player): Connection`
>
> Fires when a player leaves the server. Returns `Connection`.

#### Parameters

- `player: Player` — a player who has left the server.

## Vortex Studio 0.3.4 notes

`GetPlayers()` returns the current player in a `LocalScript`. In a confirmed
server `Script`, it also returned a list containing the live `Player` object;
that object's `Character` is readable. `LocalPlayer` remains `nil` on the
server.

The numeric connection id passed as the first `OnServerEvent` argument still
has no known public mapping back to a particular `Player`. Numeric/string service
indexing and the tested player lookup methods do not provide that mapping.
