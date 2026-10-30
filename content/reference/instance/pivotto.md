### PivotTo(targetCFrame: [`CFrame`](../datatypes/cframe.md))

> `nil`
>
> Moves the Instance so that its pivot is at `targetCFrame`. On a `Model`, every part moves with it and keeps its position relative to the pivot.
>
> ```lua
> model:PivotTo(CFrame.new(0, 20, 0))
> ```
>
> It can also be called on a `Part` and on a player's character. See [`GetPivot`](./getpivot.md).
