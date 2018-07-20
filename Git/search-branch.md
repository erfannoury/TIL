You can use git to search for all the branches that contain a given commit.

You can use the following command:
```bash
$ git branch --contains <commit-hash>
```
But this will only search local branches. By adding the `-a` flag it will search for all local and remote branches.
```bash
$ git branch -a --contains <commit-hash>
```
[Source](https://stackoverflow.com/a/43535152/5069650)
