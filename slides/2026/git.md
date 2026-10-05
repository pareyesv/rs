---
title: Introduction to GIT
date: 13 November 2025
author: Andres Aravena
---

## I am Andres Aravena

+ Senior AI Engineer at Ennova-Research (Venice)
+ Former academic at Istanbul University
+ Mathematical Engineer, U. of Chile
+ PhD Informatics, INRIA–U Rennes 1, France
+ PhD Mathematical Modeling, U. of Chile

## I used to teach Bioinformatics

That is, a mix of Biology and Informatics

Every class **50%** of my students were *bored*

+ Some said I teach obvious things
+ Some said I teach incomprehensible things

The *50%* changed every class

Today will be similar

## Version control

If you develop code (or documents in text format), you will probably keep track of it in some *Version Control System*

Advantages

1. Keep history of the project so you can change your mind
2. Serves as backup of your project *on the cloud*
3. Enable a safe way to do experiments
4. Enables collaboration with many people, remotely
5. Does not need permanent internet access

# Using git from zero {.center .good}

## In your folder

Let's say that you have a folder with your code

We need some text files. Check these websites

+ <https://www.mysamplefiles.com/download-free-md-files-samples>
+ <https://gutenberg.org/browse/scores/top>

Be sure to download *text* files

## Making a new repo

Make it a Git repository with

`git init`

Check it with

`git status`

## Introducing files to git

If you do not present a file, git will not touch it

Let's present a file with

`git add` *filename*

You can add all the folder by doing

`git add .`

(here `.` represents the current folder)

check it with `git status`. What changed?

## Take a picture

With `git add` we add files to *Stage Area*

Now we store them in the repo by doing

`git commit -m` commit-messages

If you do not use `-m`, it will open a text editor  
that opens a pandora box

## Commits

The key idea is to record **the changes** between code versions

These snapshots are called **commits**  
(identified by a long hexadecimal number)

Each commit has a **descriptive message**. Example:

+ `3e81b95` WIP
+ `da41c51` fix issues crated by cleanup
+ `1cddab7` cleanup backend (untested)
+ `484e061` small changes in tools

## Commit messages should be imperative

As if you were giving an order

That way your collaborators can know what the commit will do when applied

Which of these commit messages are clear to you?

+ WIP
+ fix issues crated by cleanup
+ cleanup backend (untested)
+ small changes in tools

## Make more changes

Change some files, add others

Check it with `git status`. What changed?

Add the changes and new files to the stage area
(how?)

Check it with `git status`. What changed?

Commit them and check it again.

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

## Advanced commands

These commands are good to know

`git bisect`

`git cherrypick`

`lazygit`

## Text editor

In the command line we use either `nano`, `code` or `vi`

probably `nano` is the best in this case

edit some files
edit `.profile` or `.bashrc`

    set EDITOR
