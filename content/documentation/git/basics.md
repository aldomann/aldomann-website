---
title: Basics
toc: true
type: book
date: "2019-12-14T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## Initial set-up

```bash
git init
git remote add origin https://github.com/aldomann/repo.git #Add Git repo to folder
git remote set-url origin git@github.com:aldomann/repo.git #Switch to SSH
git pull origin master
git branch --set-upstream-to origin/master
```

## Commands

```bash
git status -s
git add -A
git add -u
git push
```

## Garbage Clean

```bash
git gc
```

## Delete every untracked file and directory

```bash
git clean -d -f -x
```

## Remove directory from remote repository after adding them to .gitignore

```bash
git rm -r --cached some-directory
git commit -m 'Remove the now ignored directory "some-directory"'
git push origin master
```

## Reset repo when having pull conflicts

```bash
git fetch --all
git reset --hard origin/master
```

## Helpful URLs

- [Fix "Permission denied (publickey)" error when pushing with Git](https://gist.github.com/adamjohnson/5682757)
- [Connecting to GitHub with SSH](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
- [Why is Git always asking for my password?](https://help.github.com/en/github/using-git/why-is-git-always-asking-for-my-password)
