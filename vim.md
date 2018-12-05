Comment some lines:

```
:<starting line number>,<ending line number>s/^/#
```

Uncomment some lines:

```
:<starting line number>,<ending line number>s/^#/
```
[[Source](https://unix.stackexchange.com/a/120618)]

-------

To delete all lines containing a pattern `<pattern>` use:

```
:g/<pattern>/d
```

If you just use `:g/<pattern>` it will show lines that match that pattern.
