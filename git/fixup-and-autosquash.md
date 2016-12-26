# Using `--fixup` and `--autosquash`

Instead of rebasing and squashing you can do a:

```
git commit --fixup COMMIT-HASH-HERE
```

For example:

```
git commit --fixup ae3ff40ed3bbe6de2b3d96db79aa37a579401502
```

This will create a "fixup" commit, which you can then immediatelly squash by
doing an "autosquash" rebase:

```
git rebase -i --autosquash origin/master
```

This will squash all of the commits that you've "fixup" into the parent one.
