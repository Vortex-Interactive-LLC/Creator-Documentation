### WaitForChild(name: `string`, timeout: `Number?`)

> `Instance?`
>
> Waits for a child with the specified name to exist, then returns that child.
>
> If the child already exists, it is returned immediately. If the child does not exist, the function waits until it becomes available.
>
> An optional `timeout` can be provided to limit how long the function waits. If the timeout expires before the child is found, `nil` is returned.
>
> ```lua
> local part = workspace:WaitForChild("Part")
> print(part.Name)
> ```
>
> With a timeout:
>
> ```lua
> local part = workspace:WaitForChild("Part", 5)
>
> if part then
>     print("Part found")
> end
> ```
