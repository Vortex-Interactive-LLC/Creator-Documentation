---
title: Seat
description: A part a character can sit on.
---

## Summary

A `Seat` is a part a character sits on when they touch it. See the [Seats guide](../../guides/seats.md).

### Example

```luau
local seat = Instance.new("Seat")
seat.Anchored = true
seat.Parent = workspace

seat:GetPropertyChangedSignal("Occupant"):Connect(function()
    print(seat.Occupant)
end)
```

## Properties

- `Occupant` - the [`Humanoid`](./humanoid.md) sitting in the seat, or `nil`. Read-only;
- `Disabled` - `Boolean`, defaults to `false`. While `true` nobody can sit, and the current occupant is removed;
- all the properties of a [`Part`](./part.md).

## Notes

The server decides occupancy. A seat holds one character, and a character occupies one seat. The occupant is removed if they die, and a sit request from more than about 12 studs from the seat is rejected. `Humanoid.SeatPart` and the `Humanoid.Seated` signal report the same state from the character's side.
