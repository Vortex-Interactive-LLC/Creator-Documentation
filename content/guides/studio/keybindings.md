---
title: Studio Keybindings
description: Keyboard shortcuts for navigating and editing in Vortex Studio.
---

A reference for the keyboard shortcuts and mouse controls in Vortex Studio's editor.

On macOS, use `⌘` wherever a shortcut says `Ctrl`, and `Option` wherever it says `Alt`.

## File

| Shortcut | Action |
| --- | --- |
| `Ctrl` + `S` | Save |

## Editing

| Shortcut | Action |
| --- | --- |
| `Ctrl` + `Z` | Undo |
| `Ctrl` + `Y` ***or*** `Ctrl` + `Shift` + `Z` | Redo |
| `Ctrl` + `C` | Copy selected |
| `Ctrl` + `V` | Paste copied parts |
| `Ctrl` + `Shift` + `V` | Paste a copied texture onto the selected parts |
| `Ctrl` + `D` | Duplicate selected nodes/parts |
| `Ctrl` + `G` | Group selected parts into a model |
| `Shift` + `Ctrl` + `G` ***or*** `Ctrl` + `U` | Ungroup a model |
| `Alt` + `A` | Anchor or unanchor the selection. If any selected part is unanchored, all of them are anchored; otherwise they are all unanchored. Models count as the parts inside them |
| `Alt` + `L` | Lock or unlock the selection, using the same rule as anchoring |
| `F` | Focus the view on the selected parts |
| `Backspace` / `Delete` | Delete selected parts |

## Text

| Shortcut | Action |
| --- | --- |
| `Ctrl` + `A` | Select text |
| `Ctrl` + `C` | Copy text |
| `Ctrl` + `V` | Paste text |
| `Ctrl` + `X` | Cut text |

## Tools

Press a number key to activate the corresponding tool.

| Key | Tool |
| --- | --- |
| `1` | Select mode |
| `2` | Move mode |
| `3` | Rotate mode |
| `4` | Scale mode |

## Camera

| Shortcut | Action |
| --- | --- |
| `W` | Move in the direction you're looking |
| `A` | Move view left |
| `S` | Move in the opposite direction you're looking |
| `D` | Move view right |
| `Shift` + `W`/`A`/`S`/`D` | Slow camera |
| `Q` | Move camera down |
| `E` | Move camera up |
| Scroll wheel | Move the camera toward/away from where the mouse is pointing |
| `,` / `.` | Snap-rotate the view 45° left / right |
| Middle mouse + drag | Pan |
| Hold right-click + drag | Move the view |

## Selection

| Shortcut | Action |
| --- | --- |
| Left-click | Select. Clicking a part inside a model selects the whole model |
| `Alt` + click | Select the part under the cursor, even inside a model. Each further `Alt` + click on the same spot selects the next object behind the current selection |
| `Ctrl` + click | Select/unselect multiple nodes one at a time |
| `Shift` + click | Select multiple in the viewport; select everything in between in the Explorer |
| Left-click + drag on empty space | Box-select parts |
| Left-click + drag on a part | Move the part |
| `Esc` | Deselect everything |

Locked parts are skipped by viewport clicks and box selection, so clicks pass through them. Select a locked part from the Explorer instead.

## Explorer

| Shortcut | Action |
| --- | --- |
| `Ctrl` + `Shift` + `X` | Jump to the Explorer search box |
| `Ctrl` + `A` | While a search is active and the Explorer is focused, select every match |

The search box accepts names, `is:Class`, `Property = value` (for `Name`, `ClassName`, `Locked`, `Anchored`, `CanCollide`, `CanTouch`, `CanQuery` and `CastShadow`), `or`, and quoted names.

## Playtest

| Shortcut | Action |
| --- | --- |
| `Tab` | Show or hide the player list |

## Window

| Shortcut | Action |
| --- | --- |
| `F11` | Toggle fullscreen |
| `Ctrl` + `-`/`+` | Change Studio UI size |
