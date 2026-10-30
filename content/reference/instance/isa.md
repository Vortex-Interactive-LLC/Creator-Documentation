### IsA(className: `string`)

> `boolean`
>
> Returns `true` if the Instance is of the class `className` or inherits from it.
>
> ```lua
> print(part:IsA("Part"))     --> true
> print(part:IsA("BasePart")) --> true
> print(part:IsA("Instance")) --> true
> print(part:IsA("Model"))    --> false
> ```
