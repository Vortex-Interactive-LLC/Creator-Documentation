### GetAttributeChangedSignal(name: `string`)

> [`Signal`](../datatypes/signal.md)
>
> Returns a signal that fires when the attribute `name` changes.
>
> ```lua
> part:GetAttributeChangedSignal("Health"):Connect(function()
>     print("Health is now", part:GetAttribute("Health"))
> end)
> ```
>
> The signal fires on instances that are parented into the game. It does not fire for an Instance with no parent.
