---
title: Attributes
description: Attributes are custom properties that can be given to an Instance. A value can be a boolean, number, or string.
---
> [!Summary]
> Attributes let you store custom metadata on an Instance using name-value pairs. Use `SetAttribute` to create or update values, `GetAttribute` to read one value, and `GetAttributes` to inspect all stored attributes on the object.

### Methods
___________________
### SetAttribute
Creates, updates, or removes an attribute value.
```
Instance:SetAttribute(Attribute: string, Value: boolean | number | string | nil)
```
#### Parameters

```
Attribute: string
The name of the attribute being set.
```
```
Value: boolean | number | string | nil
The value to set the specified attribute to.
```

#### Returns
```
()
```
The SetAttribute method is used for modifying an attribute's value or creating a new attribute if it does not already exist. If the value given is nil, the attribute will be removed.
#### Examples
In the code snippet below, it sets the `"Id"` attribute of the Part to `1`.
```luau
local Part = workspace:WaitForChild("Part")
Part:SetAttribute("Id", 1)
```

___________________
### GetAttribute

```
Instance:GetAttribute(Attribute: string): boolean | number | string | nil
```
#### Parameters

```
Attribute: string
The name of the attribute being retrieved.
```
#### Returns
```
boolean | number | string | nil
The value assigned to the specified attribute. If no value has been assigned to the attribute, nil is returned.
```
The GetAttribute method is used for retrieving the value assigned to the specified attribute.
#### Examples
In the code snippet below, it retrieves the Id attribute and then prints it.
```luau
local Part = workspace:WaitForChild("Part")
local Id = Part:GetAttribute("Id")
print(Id)
```

___________________
### GetAttributes
GetAttributes returns a dictionary containing the attributes of an Instance.

___________________
### GetAttributeChangedSignal
```
Instance:GetAttributeChangedSignal(Attribute: string)
```

#### Parameters
```
Attribute: string
The name of the specified attribute for which the change signal is being returned. 
```
#### Returns
```
ScriptSignal
An event that fires when the specified attribute changes.
```
### Creating Attributes

Call `SetAttribute` with a new name to create an attribute. Set the same name again to update it, or pass `nil` to remove it.

```luau
local part = workspace:WaitForChild("Part")

part:SetAttribute("Id", 1)       -- create
part:SetAttribute("Id", 2)       -- update
part:SetAttribute("Id", nil)     -- remove
```

Use `GetAttributes()` when several current values are needed; it returns a table keyed by attribute name.

## Supported value types

An attribute value must be `nil`, a `boolean`, a `number`, or a `string`. Other values, such as `Vector3`, `Color3`, and tables, raise an error. Attribute names cannot be empty.

## Behavior

`SetAttribute`, `GetAttribute`, `GetAttributes`, and removal through `SetAttribute(name, nil)` work on any instance, including `Player` objects. `GetAttributes` returns a table containing the current values.

`GetAttributeChangedSignal` fires when an attribute is set on an instance that is parented into the game. It does not fire for instances that have no parent, and it does not fire for an attribute set in the same frame as the instance was parented. Wait a frame after setting `Parent` before connecting and setting values you want to observe.

A player's `Character` is an exception to the client/server boundary: attributes a server Script sets on it reach the owning client, where a LocalScript reads them through `LocalPlayer.Character:GetAttribute`. Attributes a LocalScript sets are not sent to the server.
