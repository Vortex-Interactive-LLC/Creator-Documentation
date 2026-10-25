---
title: ModuleScript
description: A non-executable runtime module shell.
---

## Runtime support

`ModuleScript` can be used in Vortex Studio 0.8.1 in both `Script` and
`LocalScript` contexts. `Source`, `Disabled`, and `RunContext` read as `nil`, and assigning
`Source` is rejected.

## Overview

A universal script that returns exactly one value, usually a table of functions, to used by other scripts.

ModuleScripts are typically placed in `ReplicatedStorage` so that they are visible in both run contexts.

## Code Samples

To activate a `ModuleScript` specify the path to it using the `require` function. 

```luau
local moduleScript = require(game:GetService('ReplicatedStorage').ModuleScript)
```

By default, a `ModuleScript` returns an empty array. Supports adding values, can be converted into a dictionary.

```luau
local module = {
	['fruits'] = {
		'banana',
		'apple',
		'orange'
	},
	['vegetables'] = {
		'cucumber',
		'corn',
		'tomato'
	},
	['amount'] = 6
}

return module
```

Also `ModuleScript` supports the creation of functions.

```luau
local module = {}

function module.foo()
	print('Foo!')
end

function module.bar()
	print('Bar!')
end

function module.quux()
	return 'Quux!'
end

return module
```
```luau
return function()
	print('Boom!')
end
```

A function in a `ModuleScript` can be called within the same `ModuleScript`.

```luau
local module = {}

function module.foo()
	print('Foo!')
end

module.foo()

return module
```
