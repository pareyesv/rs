---
title: Teaching GIT
date: 2024-10-18
author: Andres Aravena
---

## using either `nano`, `code` or `vi`

probably `nano` is the best in this case

edit some files
edit `.profile` or `.bashrc`
	set EDITOR

# Using git from zero

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

`git add` _filename_

You can add all the folder by doing

`git add .` 

(here `.` represents the current folder)

check it with `git status`. What changed?

## Take a picture

With `git add` we add files to *Stage Area*

Now we store them in the repo by doing

`git commit -m ` commit-messages

If you do not use `-m`, it will open a text editor  
that opens a pandora box

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

`git restore` _some options_

There are several options, that you can check 

`git help restore`

# Experimenting

## Experiment

`git branch`
	plain, `-v`, `-vv`, `-d`
`git switch`
`git merge`

# Collaborating

`git remote`
`git push`
`git pull`
`git clone`

`git fetch`

## teamwork

+ commit messages
+ merge request

## advanced

`git bisect`
`git cherrypick`
`lazygit`
