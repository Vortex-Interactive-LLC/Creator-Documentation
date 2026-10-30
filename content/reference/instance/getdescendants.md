### GetDescendants()

> `Array`
>
> Returns an array of all the Instance's descendants: its children, their children, and so on.
>
> ```lua
> for _, descendant in model:GetDescendants() do
>     if descendant:IsA("BasePart") then
>         descendant.Anchored = true
>     end
> end
> ```
