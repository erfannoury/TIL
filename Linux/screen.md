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

When inside an screen, you might want to detach from the screen, but the screen remain open. In that case you can use `Ctrl-A d`.

To kill an screen, when inside it, use `Ctrl-A k` and type `y`.

To scroll the output of the screen (specially after you've re-attached a screen and you want to view past content on the screen) use `Ctrl-A [`.

To get more help and information about screen, don't forget `man screen` and `Ctrl-A ?`.

## Move a running process to screen
Source: I first saw this mentioned in [this tweet](https://twitter.com/TimMedin/status/946437434933501953) which links to [this Linkedin article](https://www.linkedin.com/pulse/move-running-process-screen-bruce-werdschinski/).

Steps:
1. `Ctrl + Z` to suspend the process
2. `$ bg` to continue running the process in the background
3. `$ disown %1` to disown the process
4. `$ screen -S <screen name>`
5. `$ pgrep <process name>` to find the PID of the process
6. `$ reptyr <pid>` to take over the process
