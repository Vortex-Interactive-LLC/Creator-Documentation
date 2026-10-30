---
title: os
description: Time and date functions.
---

Only the time and date functions are available.

```lua
print(os.time())             -- seconds since 1 January 1970
print(os.clock())            -- seconds of processor time, for timing code
print(os.date("%Y-%m-%d"))   -- formatted date
print(os.difftime(10, 5))    -- 5
```

- `os.time(table?)` - returns the current time as a number of seconds. Pass a table with `year`, `month`, `day` (and optionally `hour`, `min`, `sec`) to convert a date to a number;
- `os.clock()` - returns a number of seconds, useful for measuring how long code takes;
- `os.date(format?, time?)` - formats a time. Start the format with `!` for UTC, or use `"*t"` to get a table;
- `os.difftime(t2, t1)` - returns `t2 - t1`.

`os.getenv`, `os.exit`, `os.execute`, `os.remove`, and the rest of the operating system library are not available.
