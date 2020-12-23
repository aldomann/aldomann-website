---
title: Branches
toc: true
type: book
date: "2019-12-14T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## Create local branch

To create a new branch and switch to it at the same time, you can run
```bash
git checkout -b <new-branch>
```

This is shortcut to
```bash
git branch <new-branch>
git checkout <new-branch>
```

To be able to make commits into GitHub (or whichever Git hosting service you use) you need to first push the current branch and set the remote as upstream:
```bash
git push --set-upstream origin <new-branch>
```

## Add local branch from remote branch

If your repository already has a remote branch that you want to work on locally, you can add it to your local repository by running
```bash
git checkout <remote-branch>
```

or on older verions of Git:
```bash
git checkout -b <remote-branch> origin/<remote-branch>
```

## Switch between branches

To switch between your branches and your `master` branch, you can use the
```bash
git checkout <new-branch>
```
and
```bash
git checkout master
```

## Merge branches

Before merging branches, make sure you are on the *receiving* branch (usually `master`) by running
```bash
git checkout <receiving-branch>
```
After that, you can merge your desired branch `<merged-branch>` to  `<receiving-branch>` by running
```bash
git merge <merged-branch>
```

## Delete branches

### Delete local branch

Once you've finished working on a branch and have merged it into the main code base, you're free to delete the branch without losing any history:
```bash
git branch -d <new-branch>
```

However, if the branch hasn't been merged, the above command will output an error message warning you that the branch is not fully merged.

If you really want to delete the branch, you can use the `-D` flag:

```bash
git branch -D <new-branch>
```
This deletes the branch regardless of its status and without warnings, so use it judiciously.


### Delete remote branch

```bash
git push origin --delete <remote-branch>
```
