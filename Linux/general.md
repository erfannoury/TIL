When a process can't be killed using `Ctrl + C`, one way to kill it is to search for its process id and then use `kill -9 <pid>` to kill it.

The other way (I learned it from Vipin) is to press `Ctrl + Z` to put that process in the background, and then use `kill %1` to kill that process.

----

One way to loop in bash commands is to use `{<start>..<end>}` in the arguments.
```bash
$ echo hello{1..3}
hello0 hello1 hello2

$ wget https://someplace.com/data_train_{0..10}.zip
```

----

When trying to move a large number of files using the `mv` command, it can fail, giving a "too many arguments" error. To mitigate this issue, `find` command can be used.
```bash
# From within the folder that contains a large number of files.
$ find . -name "*" -maxdepth 1 -exec mv -t <target folder> {} +
```
Note: instead of `"*"` wildcard, a restrictive one like `"*.jpg"` can also be used.

[Source](https://unix.stackexchange.com/a/102855)
