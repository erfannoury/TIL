This documents the whole workflow for removing one or more commits from a pull request. In summary, first you should reset to a previous point in history, then make changes, commit again, and then force-push to upstream.

1. Switch to the PR branch.
```
$ git checkout <pr-branch>
```

2. Find the commit hash of the last correct commit (before the wrong commit(s)).

3. Reset the git to after that point in git history.
```
$ git reset --hard <commit hash>
```
Note that this will remove every change that has happened after that last correct commit. So make sure to have the correct changes somewhere so that you can apply them again.

4. Make new changes and commit them.

5. Force-push
```
$ git push --force
```
or sometimes
```
$ git push --set-upstream origin <pr-branch> --force
```

[Source](https://stackoverflow.com/a/40780769)
