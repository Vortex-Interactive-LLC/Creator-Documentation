### GetAttribute(name: `string`)

> `boolean | number | string | nil`
>
> Returns the value of the attribute `name`, or `nil` if the attribute is not set.
>
> ```lua
> part:SetAttribute("Health", 5)
> print(part:GetAttribute("Health")) --> 5
> print(part:GetAttribute("Missing")) --> nil
> ```
>
> See [Attributes](../../guides/attributes.md).
