### SetAttribute(name: `string`, value: `boolean | number | string | nil`)

> `nil`
>
> Sets the attribute `name` to `value`. Passing `nil` removes the attribute.
>
> ```lua
> part:SetAttribute("Health", 5)
> part:SetAttribute("Health", nil)
> ```
>
> Attributes can only hold booleans, numbers, strings, or `nil`. Any other value, such as a `Vector3`, raises an error, as does an empty name.
