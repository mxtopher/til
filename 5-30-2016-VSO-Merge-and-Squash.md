VSO Pull Requests and the Merge-and-Squash option
=================================================

When you have a pull request approved in VSO, you have the option
to squash all the commits when making a merge. That way, your whole
PR will become a single commit on the merged branch.

Be aware that in the future, when you try to delete your local branches
with

```
git branch -d local-branch
```

git will complain that local-branch is not fully merged, so you will
have to use the -D option.
