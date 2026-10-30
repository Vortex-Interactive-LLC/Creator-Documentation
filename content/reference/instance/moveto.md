### MoveTo(position: [`Vector3`](../datatypes/vector3.md))

> `nil`
>
> Moves a `Model` so that its pivot is at `position`.
>
> ```lua
> model:MoveTo(Vector3.new(10, 30, 10))
> ```
>
> `MoveTo` is only available on models and characters. Calling it on a `Part` raises an error, so set the part's `Position` or use [`PivotTo`](./pivotto.md).
