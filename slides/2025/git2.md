---
title: Introduction to GIT
date: 13 November 2025
author: Andres Aravena
---

## History

Look at the history of commits

`git log`

Sometimes it is useful to say

`git log --oneline`

## Going back in time

We can recover previous versions of a file with the command

`git restore` *some options*

There are several options, that you can check

`git help restore`

# Experimenting {.center .good}

## When you are not sure if it will work

To develop new code but keep the working version, *Git* uses **branches**

In other words a commit can be followed by several new commits

This allow freedom to do experiments, and roll back if they fail

The hard part is to **keep track** and **merge** them

<!-- If two people modified the same part of a file, there will be a conflict -->

## Branches

We can create a *branch* with the command

`git branch` branch-name

Check it with

`git branch`

`git branch -v`

`git branch -vv`

What is the default branch name?

<!-- `-d` -->

## Switch to another branch

`git switch` branch-name

Check it with

`git branch`

`git branch -v`

`git branch -vv`

Old versions used `git checkout` but this can be dangerous  
(it is too powerful)

## When the experiment finishes

If things were bad, you can go back

If things go ok, you can merge into the main branch

`git switch main`

`git merge` branch-name

# Collaborating {.center .good}

## Add a remote repository

Let's go to GitHub and create an empty repo

Follow the instructions and add a remote

Check it with

`git remote`

## Interacting with remote reports

+ `git push` send your local commits to the remote repo

+ `git pull` is basically a combination of

  + `git fetch` gets commits from remote repo
  + `git merge` merge the new commit into the local repo

## Get the repository somewhere else

`git clone`

You can clone other repos

Other people can clone yours (if it is public)

## Online platforms and Issues

Git is often used with a web platform like *GitHub*, *GitLab*, *BitBucket* or similar, either public or private

These sites add extra functionality. For instance, they allow us to track **issues** with the code

They can be used to organize code development

::: {.block style="width: 80%"}
Every issue describes a missing characteristic

The title should describe **what the state should be once the issue is solved**
:::

<!-- ## Examples of issue names -->

## Branch names

A popular naming strategy is to use a prefix like `feature/` or `hotfix/`

In my experience these names are not clear enough

Online platforms allow you to create branches *from the issue page*

These branches have names corresponding to the issue

<https://github.com/anaraven/msr/issues/1>{target="_blank"}

## Visualization of branches

```
git log --graph --all --date=short
```

## Merge and conflicts

What happens if two people 

## Collaboration

+ Fork

+ Pull requests

## Advanced commands

These commands are good to know

`git bisect`

`git cherry-pick`

`lazygit`

## Text editor

In the command line we use either `nano`, `code` or `vi`

probably `nano` is the best in this case

edit some files
edit `.profile` or `.bashrc`

    set EDITOR
