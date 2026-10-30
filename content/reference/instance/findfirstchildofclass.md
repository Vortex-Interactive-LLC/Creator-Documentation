### FindFirstChildOfClass(className: `string`)

> `Instance?`
>
> Returns the first direct child whose class is `className`, or `nil` if there is none.
>
> ```lua
> local model = workspace:FindFirstChildOfClass("Model")
> local humanoid = character:FindFirstChildOfClass("Humanoid")
> ```
>
> Only direct children are searched.
