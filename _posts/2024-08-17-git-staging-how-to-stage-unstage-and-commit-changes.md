---
title: "Git Staging: How to Stage, Unstage and Commit Changes"
excerpt: "Learn how to stage, unstage, and commit changes in Git. This guide covers the essential Git commands and workflows to help you manage your source code efficiently."
date: Aug 17, 2024
layout: post
author: neha
categories:
    - git
image: assets/techalgospotlight-git-banner.webp
keywords: git staging, git stage, git unstage, git commit changes
published: true
---

Git came with exciting features like **git staging** and **git unstaging** files or **Committing** changes to a branch. As you know, We developers add, modify or delete files daily. But we have to commit to a **staging environment** whenever we complete any task or work.

Let’s understand staging, unstaging, committing work, add changes in Hunk step by step.

* * *

How to Stage All Changes to Files
---------------------------------

```bash
git add . # Version >= 2.0
```


In version 2.x, **git add .** will stage all changes to files in the current directory and all its subdirectories. However, in

1.x It will only stage new and modified files, not deleted files.

Use **git add -A**, or its equivalent command **git add --all**, to stage all changes to files in any version of git.

* * *

Unstage a file that contains changes
------------------------------------

* * *

How to Add changes by hunk
--------------------------

You can see what “**hunks**” of work would be staged for commit using the patch flag:

or

This opens an interactive prompt that allows you to look at the diffs and let you decide whether you want to include them or not.

**Stage this hunk [y,n,q,a,d,/,s,e,?]?**


|Flag|Flag usage                                                  |
|----|------------------------------------------------------------|
|y   |stage this hunk for the next commit                         |
|n   |do not stage this hunk for the next commit                  |
|q   |quit; do not stage this hunk or any of the remaining hunks  |
|a   |stage this hunk and all later hunks in the file             |
|d   |do not stage this hunk or any of the later hunks in the file|
|g   |select a hunk to go to                                      |
|/   |search for a hunk matching the given regex                  |
|j   |leave this hunk undecided, see next undecided hunk          |
|J   |leave this hunk undecided, see next hunk                    |
|k   |leave this hunk undecided, see previous undecided hunk      |
|K   |leave this hunk undecided, see previous hunk                |
|s   |split the current hunk into smaller hunks                   |
|e   |manually edit the current hunk                              |
|?   |print hunk help                                             |


_This makes it easy to catch changes that you do not want to commit._

You can also open this via **git add** -- interactive and selecting p.

* * *

Interactive add in Git
----------------------

**git add** -i (or --interactive) will give you an interactive interface where you can edit the index, to prepare what you want to have in the next commit. You can add and remove changes to whole files, add untracked files and remove files from being tracked, but also select subsections of changes to put in the index, by selecting chunks of changes to be added, splitting those chunks, or even editing the diff. Many graphical commit tools for Git (like e.g. **git gui**) include such a feature; this might be easier to use than the command line version.

It is very useful (1) if you have entangled changes in the working directory that you want to put in separate commits and not all in one single commit and (2) if you are in the middle of an interactive rebase and want to split too large a commit.

```bash
$ git add -i
              staged        unstaged path 
1:         unchanged        +4/-4 index.js
2:             +1/-0       nothing package.json

*** Commands ***
  1: status  2: update  3: revert  4: add untracked
  5: patch  6: diff  7: quit  8: help
What now>
```


The top half of this output shows the current state of the index broken up into staged and unstaged columns:

*   **index.js** has had 4 lines added and 4 lines removed. It is currently not staged, as the current status reports “unchanged.” When this file becomes staged, the +4/-4 bit will be transferred to the staged column and the unstaged column will read “nothing.”
*   **package.json** has had one line added and has been staged. There are no further changes since it has been staged as indicated by the “nothing” line under the unstaged column.
*   The bottom half shows what you can do. Either enter a number (1-8) or a letter (s, u, r, a, p, d, q, h).
*   **status** shows output identical to the top part of the output above.
*   **update** allows you to make further changes to the staged commits with additional syntax.
*   **revert** will revert the staged commit information back to HEAD.
*   **add untracked** allows you to add file paths previously untracked by version control.
*   **patch** allows for one path to be selected out of an output similar to the status for further analysis.
*   **diff** displays what will be committed.
*   **quit** exits the command.
*   **help** presents further help on using this command.

* * *

How to show Staged Changes
--------------------------

To display the hunks that are staged for commit:

* * *

Staging A Single File in Git
----------------------------

To stage a file for committing, run

* * *

Stage deleted files in Git
--------------------------

To delete the file from git without removing it from the disk, use the **--cached** flag