When submitting a PR to a library, after being finalized, it is better to squash all commits into a single commit. To do so use these commands: (as suggested by f0k)

```
git reset <commit hash>  # set HEAD to the first commit of this PR
git commit -a --amend -m <commit message>  # amend all other changes to that commit
git push --force origin HEAD  # overwrite PR with the new clean history
```
