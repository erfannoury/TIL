To output (and write to file) both stdout and stderr, use the following command:
```bash
<command> > >(tee stdout.log) 2> >(tee stderr.log >&2)
```

[Source](http://stackoverflow.com/a/692407/5069650)
