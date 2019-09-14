When a local branch falls behind the master branch, `git rebase` can be used to bring the latest changes to the local branch.

To initiate a rebase, first the following command should be executed:
```
$ git rebase origin/master
```

In all subsequent steps, you should note the messages that `git` shows after each command to know which new commands need to be executed.

Git `rebase` will get new changes and try to merge them into the local files. This may result in conflicts. Conflicts should be resolved manually (if the `rebase` was interrupted, it is due to merge conflicts that couldn't be resolved automatically).

After resolving a conflict, the following command needs to be used to add the resolved conflict to git.
```
$ git add <filename>
```

After resolving all the conflicts at the current stage, use
```
$ git rebase --continue
```
to continue with the `rebase`.

Sometimes a change is introduced in git rebase that had been applied before. In that case you can use
```
$ git rebase --skip
```
for that particular change (which resulted in a conflict).

In some rare occasions, `git rebase` is not proceeding correctly. In that case you can use the following command to cancel the `rebase` operation and get back to the state before you first executed `git rebase ...`:
```
$ git rebase --abort
```
