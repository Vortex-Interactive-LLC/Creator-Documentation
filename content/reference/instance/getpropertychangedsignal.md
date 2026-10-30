### GetPropertyChangedSignal(property: `string`)

> [`Signal`](../datatypes/signal.md)
>
> Returns a signal that fires after the property `property` changes.
>
> ```lua
> part:GetPropertyChangedSignal("Transparency"):Connect(function()
>     print("Transparency is now", part.Transparency)
> end)
> ```
>
> The signal fires on instances that are parented into the game. It does not fire for an Instance with no parent. A property name that does not exist does not raise an error, but its signal never fires.
