---
title: Runtime standard libraries
description: Standard-library functions verified in Vortex.
---

> [!Summary]
> This page documents standard-library functions available in Vortex. It lists tested `coroutine`, `math`, `string`, and `table` functions, along with observed behavior and unavailable library features.

## Verified runtime compatibility

The following standard-library functions are available in both `Script` and `LocalScript`.

### coroutine

`close`, `create`, `isyieldable`, `resume`, `running`, `status`, `wrap`, `yield`

### math

`abs`, `acos`, `asin`, `atan`, `atan2`, `ceil`, `clamp`, `cos`, `cosh`, `deg`, `exp`, `floor`, `fmod`, `frexp`, `ldexp`, `lerp`, `log`, `log10`, `map`, `max`, `min`, `modf`, `noise`, `pow`, `rad`, `random`, `randomseed`, `round`, `sign`, `sin`, `sinh`, `sqrt`, `tan`, `tanh`

### string

`byte`, `char`, `find`, `format`, `gmatch`, `gsub`, `len`, `lower`, `match`, `pack`, `packsize`, `rep`, `reverse`, `split`, `sub`, `unpack`, `upper`

### table

`clear`, `clone`, `concat`, `create`, `find`, `foreach`, `foreachi`, `freeze`, `getn`, `insert`, `isfrozen`, `maxn`, `move`, `pack`, `remove`, `sort`, `unpack`

## Observed deterministic behavior

These are observations for the exact inputs tested through a local script, rather than a claim that the full Luau standard-library contract is implemented.

### coroutine

- `close` on a suspended coroutine returned `true` and left it `dead`.
- `create` returned a `thread`; `isyieldable()` returned `true`; a fresh coroutine reported `suspended`.
- `resume` returned `true, 42` for a coroutine that added one to `41`; `wrap` returned `42` for a coroutine that doubled `21`; and `yield` returned `true, "yielded"` from its first `resume`.
- Inside a coroutine, `running()` returned a `thread` and a `nil` main-thread flag.

### table

| Call | Observed result |
| --- | --- |
| `clear({1, 2})` | length `0` |
| `clone({value = 5})`, then mutate clone | source `5`; clone `7` |
| `concat({"a", "b", "c"}, "-")` | `"a-b-c"` |
| `create(3, "x")` | length `3`; first/last `"x"` |
| `find({"a", "b"}, "b")` | `2` |
| `foreach({a = 2, b = 3}, ...)` / `foreachi({2, 3}, ...)` | sum `5` / `5` |
| `freeze({1})`, then `isfrozen` | `true` |
| `getn({1, 2, 3})` | `3` |
| `insert({1, 3}, 2, 2)` | `"1,2,3"` |
| `maxn({[2] = true, [5] = true})` | `5` |
| `move({"a", "b"}, 1, 2, 3, {})` | destination `"a", "b"` at `3`, `4` |
| `pack("a", nil, "c")` | `n = 3`; values `"a"`, `"c"` |
| `remove({"a", "b"}, 1)` | removed `"a"`; remaining length `1`, first `"b"` |
| `sort({3, 1, 2})` | `"1,2,3"` |
| `unpack({"a", "b"})` | `"a", "b"` |

### string

| Call | Observed result |
| --- | --- |
| `byte("A")`; `char(65, 66)` | `65`; `"AB"` |
| `find("vortex", "tex")`; `format("%s:%d", "vortex", 7)` | `4, 6`; `"vortex:7"` |
| `gmatch("a,b", "[^,]+")`; `gsub("a-b", "-", "+")` | `"a", "b"`; `"a+b", 1` |
| `len`, `lower`, `match` | `6`; `"vortex"`; `"tex"` |
| `pack("<I2", 300)`; `packsize("<I2")` | byte length `2`; `2` |
| `rep("ab", 3)`; `reverse("vortex")` | `"ababab"`; `"xetrov"` |
| `split("a,b", ",")`; `sub("vortex", 2, 4)` | `2, "a", "b"`; `"ort"` |
| `unpack("<I2", pack("<I2", 300))`; `upper("VoRtEx")` | `300, 3`; `"VORTEX"` |

### math

| Call | Observed result |
| --- | --- |
| `abs(-3)`, `ceil(1.2)`, `floor(1.8)`, `round(1.5)`, `sign(-5)` | `3`, `2`, `1`, `2`, `-1` |
| `acos(0.5)`, `asin(0.5)`, `atan(1)`, `atan2(1, 1)` | `1.0471975511965979`, `0.5235987755982989`, `0.7853981633974483`, `0.7853981633974483` |
| `clamp(5, 0, 3)`, `cos(0)`, `cosh(0)`, `deg(pi)` | `3`, `1`, `1`, `180` |
| `exp(1)`, `fmod(-7, 3)`, `frexp(8)`, `ldexp(0.5, 4)` | `2.718281828459045`, `-1`, `0.5, 4`, `8` |
| `lerp(0, 10, 0.25)`, `log(8)`, `log10(1000)`, `map(0.25, 0, 1, 0, 100)` | `2.5`, `2.0794415416798357`, `3`, `25` |
| `max(1, 5, 3)`, `min(1, 5, 3)`, `modf(1.25)` | `5`, `1`, `1, 0.25` |
| `noise(0.25, 0.5, 0.75)`, `pow(2, 3)`, `rad(180)` | `-0.2697153091430664`, `8`, `3.141592653589793` |
| `random()` | a `number` |
| `sin(0)`, `sinh(0)`, `sqrt(9)`, `tan(0)`, `tanh(0)` | `0`, `0`, `3`, `0`, `0` |
| `randomseed(12345)` | no return values |

## Testing Notes

The following are not available in Script or LocalScript and read as `nil`: `bit32`, `buffer`, `debug`, `utf8`, `vector`, and `shared`. The `os` library only provides `os.time`, `os.clock`, `os.date`, and `os.difftime`. `math.isfinite`, `math.isinf`, `math.isnan`, `task.desynchronize`, and `task.synchronize` are also `nil`.
