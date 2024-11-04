---
title: "Mastering Git Diff: An Ultimate Friendly Guide in 2024"
excerpt: "Unlock the secrets of Git Diff with this comprehensive guide. Learn how to track changes in your codebase with ease using Git Diff commands and techniques."
date: Aug 23, 2024
layout: post
author: neha
categories:
    - git
image: assets/techalgospotlight-git-banner.webp
keywords: git diff, git diff command, git diff example, git diff tool, git diff options 
published: true
tags: featured
---

Are you curious about the mysteries of **Git Diff**? Do you want to unlock the secrets of tracking changes in your codebase with ease? Look no further! Git Diff is a powerful tool that helps you understand the changes made to your code, and in this article, we’ll take you on a journey to master it. Whether you’re a seasoned developer or just starting out, this comprehensive guide will walk you through the various Git Diff commands and techniques, helping you to become a version control virtuoso. So, let’s dive in and discover the wonders of Git Diff together!

* * *

Git Diff Can Show Difference in Working Branch
----------------------------------------------

This will show the unstaged changes on the current branch from the commit before it. It will only show changes relative to the index, meaning it shows what you could add to the next commit, but haven’t. To add (stage) these changes, you can use **git add**.

If a file is staged but was modified after it was staged, **git diff** will show the differences between the current file and the staged version.

* * *

Git Diff Can Show Changes Between Two Commit
--------------------------------------------

```bash
git diff 1234abc..6789def # old new
```


E.g.: Show the changes made in the last 3 commits:

```bash
git diff @~3..@ # HEAD -3 HEAD
```


> **Note**: the two dots (..) is optional, but adds clarity.

Git diff will show the textual difference between the commits, regardless of where they are in the tree.

* * *

Git Diff Can Show Differences in Staged Files
---------------------------------------------

This will show the changes between the previous commit and the currently staged files.

> **NOTE**: You can also use the following commands to accomplish the same thing:

Which is just a synonym for **–staged** or

Git diff will trigger the verbose settings of the status command.

* * *

Git Diff Can Compare Branches
-----------------------------

Show the changes between the tip of the **new** and the tip of the **original** using git diff.

```bash
git diff original new # equivalent to original..new
```


Show all changes on the **new** since it branched from the **original**:

```bash
git diff original...new # equivalent to $(git merge-base original new)..new
```


Using only one parameter such as **git diff original** is equivalent to **git diff original..HEAD**.

* * *

Git Diff Can Show Both Staged and Unstaged Changes
--------------------------------------------------

To show all staged and unstaged changes in git diff, use:

> **NOTE**: You can also use the following command:

The difference is that the output of the latter will tell you which changes are staged for commit and which are not in git diff.

* * *

Git Diff Can Show Differences in Specific Directory or File
-----------------------------------------------------------

Git diff shows the changes between the previous commit of the specified file **(myfile.txt)** and the locally modified version that has not yet been staged.

Also same for the Directory

The above shows the changes between the previous commit of all files in the specified directory (documentation/) and the locally-modified versions of these files, that have not yet been staged in git diff.

To show the difference between some version of a file in a given commit and the local HEAD version you can specify the commit you want to compare against:

```bash
git diff 27fa75e myfile.txt
```


Or if you want to see the version between two separate commits:

```bash
git diff 27fa75e ada9b57 myfile.txt
```


To show the difference between the version specified by the hash **ada9b57** and the latest commit on the branch **my\_branchname** for only the relative directory called **my\_changed\_directory/** you can do this:

```bash
git diff ada9b57 my_branchname my_changed_directory/
```


* * *

Git Diff Can Help to View a **word-diff** for Long Lines
------------------------------------------------------

```bash
git diff [HEAD|--staged...] --word-diff
```


Rather than displaying lines changed, this will display differences within lines in git diff. For example, rather than:

```bash
-Hello world 
+Hello world!
```


Where the whole line is marked as changed, **word-diff** alters the output to:

```bash
Hello [-world-]{+world!+}
```


You can omit the markers \[-, -\], {+, +} by specifying **--word-diff**\=color or **--color-words**. This will only use colour coding to mark the difference:

* * *

Git Diff Can Show Differences in the Current and Last Version
-------------------------------------------------------------

Git diff will show the changes between the previous and current commits.

* * *

Git Diff Can Produce a patch-compatible diff
--------------------------------------------

Sometimes you just need a diff to apply using the patch. The regular **git --diff** does not work. Try this instead:

```bash
git diff --no-prefix > some_file.patch
```


You can reverse it.

```bash
patch -p0 < some_file.patch
```


* * *

Git Diff Can Modify a Working Directory using meld
--------------------------------------------------

```bash
git difftool -t meld --dir-diff
```


will show the working directory changes.

```bash
git difftool -t meld --dir-diff [COMMIT_A] [COMMIT_B]
```


will show the differences between 2 specific commits.

* * *

Git Diff Cheatsheet
-------------------

* Parameter: -p, -u, –patch
  * Details: Generate patch
* Parameter: -s, –no-patch
  * Details: Suppress diff output. Useful for commands like git show that show the patch by default, or to cancel the effect of –patch
* Parameter: –raw
  * Details: Generate the diff in raw format
* Parameter: –diff-algorithm=
  * Details: Choose a diff algorithm. The variants are as follows: Myers, minimal, patience, histogram
* Parameter: –summary
  * Details: Output a condensed summary of extended header information such as creations, renames and mode changes
* Parameter: –name-only
  * Details: Show only names of changed files
* Parameter: –name-status
  * Details: Show names and statuses of changed files The most common statuses are M (Modified), A (Added), and D (Deleted)
* Parameter: –check
  * Details: Warn if changes introduce conflict markers or whitespace errors. What are considered whitespace errors are controlled by the core. whitespace configuration. By default, trailing whitespaces (including lines that solely consist of whitespaces) and a space character that is immediately followed by a tab character inside the initial indent of the line are considered whitespace errors. Exits with non-zero status if problems are found. Not compatible with –exit-code
* Parameter: –full-index
  * Details: Instead of the first handful of characters, show the full pre- and post-image blob object names on the “index” line when generating patch format output
* Parameter: –binary
  * Details: In addition to –full-index, output a binary diff that can be applied with git apply
* Parameter: -a, –text
  * Details: Treat all files as text.
* Parameter: –color
  * Details: Set the colour mode; i.e. use –color=always if you would like to pipe a diff to less and keep git’s colouring