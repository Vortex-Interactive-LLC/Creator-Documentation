---
title: Seats
description: Let players sit down, and find out who is sitting.
---
A [`Seat`](../reference/classes/seat.md) is a part players can sit on. Place one in the world and a player who touches it sits down.

```luau
local seat = Instance.new("Seat")
seat.Anchored = true
seat.Position = Vector3.new(0, 2, 5)
seat.Parent = workspace
```

## Who is sitting

`seat.Occupant` is the [`Humanoid`](../reference/classes/humanoid.md) of the character sitting in the seat, or `nil` when it is empty. The server decides who sits where, so there is never more than one occupant, and a character occupies at most one seat.

```luau
seat:GetPropertyChangedSignal("Occupant"):Connect(function()
    local humanoid = seat.Occupant
    print(humanoid and "someone sat down" or "the seat is empty")
end)
```

From the humanoid's side, `humanoid.SeatPart` is the seat being used, or `nil`, and `humanoid.Seated` fires with `(active, seatPart)` when the character sits or stands.

```luau
humanoid.Seated:Connect(function(active, seatPart)
    if active then
        print("sat on", seatPart.Name)
    else
        print("stood up")
    end
end)
```

## Disabling a seat

Set `Disabled` to `true` to stop anyone sitting. A character already in the seat is removed from it.

```luau
seat.Disabled = true
```

A character is also removed from the seat when they die. A sit request from a player who is too far from the seat (about 12 studs from its edge) is rejected.
