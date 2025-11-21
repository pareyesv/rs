---
title: GIT, second part
date: 21 November 2025
author: Andres Aravena
---

## History

Look at the history of commits

```sh
git log
```

Sometimes it is useful to say

```sh
git log --oneline
```

## Going back in time

We can recover previous versions of a file with the command

`git restore` *some options*

There are several options, that you can check

```sh
git help restore
```

The help pages are your friends

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

```sh
git branch

git branch -v

git branch -vv
```

What is the default branch name?

<!-- `-d` -->

## Switch to another branch

`git switch` branch-name

Check it with

```sh
git branch

git branch -v

git branch -vv
```

Old versions used `git checkout` but this can be dangerous  
(it is too powerful)

## Branch names

A popular naming strategy is to use a prefix like `feature/` or `hotfix/`

+ `feature/new-thing`
+ `hotfix/problem-to-solve`

There are also two *protected* branches:

+ `develop`, where the development happens
+ `main`, where the current official version is tracked

## Visualization of branches

```sh
git log --graph

git log --graph --oneline

git log --graph --oneline --all
```

## When the experiment finishes

If things were bad, you can go back

```sh
git switch main
```

If things go ok, you can merge into the main branch

`git switch main`

`git merge` branch-name

## Merge produces headaches

We can categorize merge problems into three stages:

1. **Before**: Preparation failures

2. **During**: Conflicts, Wrong Direction

3. **After**: Fast-forwards, Logic bugs, Reverts

## The "Dirty" Directory problem

If we have uncommitted changes in the current branch, git will not merge.

**Error Message:**

```text
error: Your local changes to the following files would be overwritten by merge
```

It avoids overwriting the files

We must commit before merging, and this will produce a *merge commit*

## Conflicts

What happens if two branches change the same file?

Usually there is no problem

Unless both change the same line. Git cannot decide which one is correct.

:::notes
edited the exact same line in a file, or one person edited a file and the other deleted it
:::

**Error Message:**

```
CONFLICT (content): Merge conflict in <file>...
Automatic merge failed; fix conflicts and then commit the result.
```

## Fixing the conflict

Open the file. Look for the markers:

```text
<<<<<<< HEAD
Title: Beta
=======
Title: Alpha
>>>>>>> main
```

**Action:** Delete the markers, choose the text you want, save, `git add`, and `git commit`.

## Panic Mode

You hit a conflict.

You panic.

You try to switch branches to check something else.

```bash
git checkout main
```

```
error: you need to resolve your current index first
```

You are trapped in `(MERGING)` mode.

## The Eject Button

If you want to give up and go back to exactly how things were before you typed merge:

```bash
git merge --abort
```

## Logical Conflicts

+ **Branch A:** Renames `calculateTax()` to `getTax()`.
+ **Branch B:** Writes new code calling `calculateTax()`.

Git merges successfully! (Different lines/files).

The app fails at runtime: `Uncaught TypeError: calculateTax is not a function`.

**Git merges text, not logic.**
A clean merge does not mean working code.
*Always run automated tests after merging.*

## The Wrong Direction

You want to bring `feature` into `main`.

**Mistake:** You are sitting on `feature` and run `git merge main`

+ `feature` gets polluted with `main` code.
+ `main` stays outdated.

Check your branch *before* merging.

```bash
git checkout main
git merge feature-branch
```

## Binary File Conflicts

Two branches edited `hero.png` (an image)

```text
warning: Cannot merge binary files: hero.png
CONFLICT (content): Merge conflict in hero.png
```

You cannot edit "pixels" inside a text editor

You must pick a winner

## Choose one binary file

Keep MY version

```bash
git checkout --ours hero.png
```

Keep THEIR version

```bash
git checkout --theirs hero.png
```

Then add and commit

```bash
git add hero.png
git commit
```

# Collaborating {.center .good}

## Add a remote repository

Let's go to GitHub and create an empty repo

Follow the instructions and add a remote

Check it with

```bash
git remote -v
```

## Interacting with remote repositories

+ `git push` send your local commits to the remote repo

+ `git pull` is basically a combination of

  + `git fetch` gets commits from remote repo
  + `git merge` merge the new commit into the local repo

## Get the repository somewhere else

`git clone` remote-repo-url

You can clone other repos

Other people can clone yours (if it is public)

## Online platforms and Issues

Git is often used with a web platform like *GitHub*, *GitLab*, *BitBucket* or similar, either public or private

These sites add extra functionality. For instance, they allow us to track **issues** with the code

They can be used to organize code development

+ Why this code is being developed
+ Who is responsabile
+ How the issues were solved

## Issues: interaction with the final users

Every issue describes a missing characteristic

The title should describe **what the state should be once the issue is solved**

<!-- ## Examples of issue names -->

## Documenting branches

In my experience names like `feature/new-thing` are not clear enough

Online platforms allow you to create branches *from the issue page*

These branches have names corresponding to the issue

<https://github.com/anaraven/msr/issues/1>{target="_blank"}

## Permissions

Imagine you want to fix a bug in an open-source project.

+ You cannot run `git push` to their repository.
+ You don't have permission
+ If everyone could write to the official code, it would be chaos.

## Forking

A **Fork** is a server-side clone. You tell GitHub: *"Take this repository and make a copy of it under **my** account."*

+ **Original Repo:** `facebook/react` (Read-Only for you)
+ **Your Fork:** `your-username/react` (Read/Write for you)

Imagine a Google Doc that is "View Only." You cannot edit it.  
So, you go to **File > Make a Copy**.  
Now you have an exact duplicate that belongs to you, and you can edit it however you want.  
The original document remains untouched.  

## What is a Fork?

+ **Git** doesn't know what a fork is. It's a **GitHub** feature.
+ A **Fork** is a copy of a repository under **your** account.
+ **Why?** You don't have permission to push to `facebook/react`. But you *can* push to `your-name/react`.

## Three repositories to watch

1. **Upstream:** The original repo (Read-Only).
2. **Origin:** Your Fork (Read/Write).
3. **Local:** Your computer.

## Step-by-Step Flow

1. **Fork:** Click the "Fork" button on GitHub. (Creates `origin`).
2. **Clone:** Clone *your fork* to your computer.
    + `git clone https://github.com/your-name/repo.git`
3. **Branch:** Create a feature branch on your computer.
    + `git checkout -b fix-typo`
4. **Commit:** Do the work and save it.
5. **Push:** Push the work *to your fork* (`origin`).
    + `git push origin fix-typo`
    + *Note:* You cannot push to Upstream!

## Pull Request (PR)

Now that your code is on your Fork, the original maintainer doesn't know about it yet. You need to tell them.

A **Pull Request** is a notification you send to the original maintainer saying:

> *"I have made changes on my fork. Please **PULL** these changes into your repository."*

## It is a Request to Merge

Behind the scenes, a PR is simply a nice UI for a `git merge`. It allows the maintainers to:

+ See the Diff (the changes).
+ Comment on specific lines of code (Code Review).
+ Run automated tests.
+ Click a green button to "Merge" (or close it if they hate it).

You took the "View Only" Google Doc, made a copy, and fixed a spelling error. You now email the owner of the original doc: *"Hey, here is a link to my copy where I fixed that typo. If you like it, copy/paste it into your original."*

## Big Picture

| Feature | Scope | Who owns it? | Action |
| :-- | :---- | :--- | :---------- |
| **Clone** | Local (Your PC) | You | Downloads files to your machine. |
| **Fork** | Server (GitHub) | You | Copies a repo to your GitHub account. |
| **Branch** | Local or Server | You | Creates a parallel version of code. |
| **PR** | Server (GitHub) | Shared | Asks to merge two branches/forks. |

## Big picture

**Flow:**  
Upstream -> (Fork) -> Origin -> (Clone) -> Local -> (Push) -> Origin -> (PR) -> Upstream

**Never submit a PR from your `main` branch.**

+ Always create a specific branch (e.g., `fix-login-bug`).
+ Why? So you can work on multiple PRs at once without mixing them up.

## Updating a PR

+ **Scenario:** A maintainer asks for changes.
+ **Do NOT:** Close the PR or create a new one.
+ **DO:** Make changes locally, commit, and `git push`.
+ **Magic:** The PR on GitHub updates automatically

# Advanced commands {.center .good}

## These commands are good to know

`git bisect`: find in which commit a bug appeared

`git cherry-pick`: take a commit from one branch and apply to another

`lazygit`: text user interface. Remember commands for you

<!-- ## Text editor

In the command line we use either `nano`, `code` or `vi`

Probably `nano` is the best in this case

edit `.profile` or `.bashrc` and set the environment variable `EDITOR` -->

<style>
  .reveal pre .bash {font-size: 40px}
</style>
