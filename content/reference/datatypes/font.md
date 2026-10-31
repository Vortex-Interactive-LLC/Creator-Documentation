---
title: Font
description: A font family with a weight and a style.
---

## Summary

A `Font` names a font family. Use it with [`GetTextBoundsParams`](../classes/get-text-bounds-params.md) and [`TextService`](../classes/text-service.md). The bundled families are the values of `Enum.Font`.

Text labels still use the `Font` property with an `Enum.Font` value. Weight and style are stored on the `Font` but not drawn yet, since the bundled families only come in a regular weight.

## Constructors

- `Font.new(family: string, weight: Enum.FontWeight?, style: Enum.FontStyle?): Font` - `weight` defaults to `Regular` and `style` to `Normal`;
- `Font.fromEnum(font: Enum.Font): Font` - the font for an `Enum.Font` value;
- `Font.fromName(name: string, weight: Enum.FontWeight?, style: Enum.FontStyle?): Font` - the font for a family name such as `"Fredoka"`;
- `Font.fromId()` - custom font assets are not supported yet, so this always raises an error.

## Properties

- `Family: string` - the family name, such as `Fredoka`;
- `Weight: Enum.FontWeight`;
- `Style: Enum.FontStyle`;
- `Bold: boolean` - `true` when the weight is `Bold` or heavier.
