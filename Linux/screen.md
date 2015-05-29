To create resumable ssh sessions, one can use the `screen` command. You can create a session using this command that won't terminate when terminal is closed or ssh session is terminated.

To create a new session, one can use this command:
```
$ screen -S _sessionname_
```

Each session can have upto 10 shells, numbered from 0 to 9, between which one can switch by pressing `Ctrl-A` and then typing the shell number, i.e. `Ctrl-A 0` to switch to first shell.

To resume a previously created session, one can enter this command:
```
$ screen -d -R _sessionname_
```

This will detach the session and reattach to the session in the current context.

To get more help and information about screen, don't forget `man screen` and `Ctrl-A ?`.