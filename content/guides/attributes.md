---
title: Attributes
description: Attributes are basically custom properties that can be given to an Instance. These properties can be any of the supported Variant data types.

Note: Variant = Any type.
---
> [!Summary]
> Attributes let you store custom metadata on an Instance using name-value pairs. Use `SetAttribute` to create or update values, `GetAttribute` to read one value, and `GetAttributes` to inspect all stored attributes on the object.

### Methods
___________________
### SetAttribute
Creates, updates, or removes an attribute value.
```
Instance:SetAttribute(Attribute: string, Value: Variant)
```
#### Parameters

```
Attribute: string
The name of the attribute being set.
```
```
Value: Variant
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
Instance:GetAttribute(Attribute: string): Variant
```
#### Parameters

```
Attribute: string
The name of the attribute being retrieved.
```
#### Returns
```
Variant
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

## Vortex Studio 0.3.4 notes

`SetAttribute`, `GetAttribute`, `GetAttributes`, and removal through `SetAttribute(name, nil)` are confirmed to work on  `Part` instances. `GetAttributes` returns a table containing the current values.

`GetAttributeChangedSignal` returns a connectable signal, but setting or removing a Part attribute did not trigger the callback in the tested runtime. Do not rely on that signal for game logic until callback delivery is confirmed.

`Player` instances do not support attributes in 0.3.4: `GetAttribute`, `GetAttributes`, `SetAttribute`, and `GetAttributeChangedSignal` all read as `nil` in both client and server contexts.

The current player's `Character` model is an important exception to the client/server boundary: a confirmed server Script set a temporary Character attribute to `42`, then `25`; a LocalScript observed both values by polling `LocalPlayer.Character:GetAttribute`. Server-to-client Character attribute replication is therefore confirmed. Use polling rather than `GetAttributeChangedSignal`, whose callback delivery remains unconfirmed.

Client-to-server Character attribute replication is also confirmed for value changes: a LocalScript set the value to `42`, then `25`, and a server Script observed both transitions through `Players:GetPlayers()[1].Character:GetAttribute`. Do not treat these attributes as trusted client input; a client can write values that the server sees.
