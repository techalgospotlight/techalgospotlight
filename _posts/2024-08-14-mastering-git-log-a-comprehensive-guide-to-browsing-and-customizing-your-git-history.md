---
title: "Mastering Git Log: A Comprehensive Guide to Browsing and Customizing Your Git History"
excerpt: "Learn how to master Git log and customize your project's commit history with precision and clarity. This guide covers essential Git log commands and techniques to help you navigate and tailor your Git logs effectively."
date: Aug 14, 2024
layout: post
author: neha
categories:
    - git
image: assets/techalgospotlight-git-banner.webp
keywords: git log, git history, git log customization, git log filtering
published: true
---

Browsing the history of a Git repository is essential for understanding the evolution of a project, tracking changes, and collaborating effectively with team members. Git provides a powerful set of tools through the **git log** command, allowing developers to view and customize their project’s commit history in various ways.

Whether you’re interested in viewing a simple log, filtering commits based on certain criteria, or even visualizing the contributions of different authors, mastering these commands will greatly enhance your workflow. This article will guide you through a comprehensive list of techniques to navigate and tailor your Git logs, making it easier to find the information you need with precision and clarity.

* * *

Basic Git Log Command
---------------------

will display all your commits with the author and hash. This will be shown over multiple lines per commit. (If you wish to show a single line per commit, look at onelineing). Use the **q** key to exit the log.

> By default, with no arguments, git log lists the commits made in that repository in reverse chronological order – that is, the most recent commits show up first. As you can see, this command lists each commit with its SHA-1 checksum, the author’s name and email, the date written, and the commit message. – **source**

Example (from **Free Code Camp** repository):

```bash
commit 87ef97f59e2a2f4dc425982f76f14a57d0900bcf
Merge: e50ff0d eb8b729
Author: Brian
Date: Thu Mar 24 15:52:07 2016 -0700

Merge pull request #7724 from BKinahan/fix/where-art-thou

Fix 'its' typo in Where Art Thou description

commit eb8b7298d516ea20a4aadb9797c7b6fd5af27ea5
Author: BKinahan
Date: Thu Mar 24 21:11:36 2016 +0000

Fix 'its' typo in Where Art Thou description

commit e50ff0d249705f41f55cd435f317dcfd02590ee7
Merge: 6b01875 2652d04
Author: Mrugesh Mohapatra
Date: Thu Mar 24 14:26:04 2016 +0530

Merge pull request #7718 from deathsythe47/fix/unnecessary-comma

Remove unnecessary comma from CONTRIBUTING.md
```


If you wish to limit your command to the last n commits log you can simply pass a parameter. For example, if you wish to list the last 2 commits logs.

* * *

Log Formatting with Prettier Log
--------------------------------

To see the log in a prettier graph-like structure use:

```bash
git log --decorate --oneline --graph
```


sample output :

```bash
* e0c1cea (HEAD -> maint, tag: v2.9.3, origin/maint) Git 2.9.3
* 9b601ea Merge branch 'jk/difftool-in-subdir' into maint
|\
| * 32b8c58 difftool: use Git::* functions instead of passing around state
| * 98f917e difftool: avoid $GIT_DIR and $GIT_WORK_TREE
| * 9ec26e7 difftool: fix argument handling in subdirs
* | f4fd627 Merge branch 'jk/reset-ident-time-per-commit' into maint
...
```


Since it’s a pretty big command, you can assign an alias:

```bash
git config --global alias.lol "log --decorate --oneline --graph"
```


To use the alias version:

```bash
# history of current branch :
git lol

# combined history of active branch (HEAD), develop and origin/master branches :
git lol HEAD develop origin/master

# combined history of everything in your repo :
git lol --all
```


* * *

Adding Color to Your Git Logs
-----------------------------

```bash
git log --graph --pretty=format:'%C(red)%h%Creset -%C(yellow)%d%Creset %s %C(green)(%cr) %C(yellow)<%an>%Creset'
```


The format option allows you to specify your log output format:


|Parameter     |Details                                           |
|--------------|--------------------------------------------------|
|%C(color_name)|option colors the output that comes after it      |
|%h or %H      |abbreviates commit hash (use %H for complete hash)|
|%Creset       |resets colour to default terminal colour          |
|%d            |ref names                                         |
|%s            |subject [commit message]                          |
|%cr           |committer date, relative to current date          |
|%an           |author name                                       |


* * *

Displaying a Compact Oneline Log
--------------------------------

will show all of your commits with only the first part of the hash and the commit message. Each commit will be in a single line, as the **oneline** flag suggests

> The oneline option prints each commit on a single line, which is useful if you’re looking at a lot of commits. – **source**

Example (from the **Free Code Camp** repository, with the same section of code from the other example):

```bash
87ef97f Merge pull request #7724 from BKinahan/fix/where-art-thou
eb8b729 Fix 'its' typo in Where Art Thou description
e50ff0d Merge pull request #7718 from deathsythe47/fix/unnecessary-comma
2652d04 Remove unnecessary comma from CONTRIBUTING.md
6b01875 Merge pull request #7667 from zerkms/patch-1
766f088 Fixed assignment operator terminology
d1e2468 Merge pull request #7690 from BKinahan/fix/unsubscribe-crash
bed9de2 Merge pull request #7657 from Rafase282/fix/
```


If you wish to limit your command to the last n commits log you can simply pass a parameter. For example, if you wish to list the last 2 commits logs.

* * *

Searching Through Git Logs
--------------------------

```bash
git log -S"#define SAMPLES"
```


Searches for **addition** or **removal** of specific string or the string matching provided **REGEXP**. In this case, we’re looking for addition/removal of the string **#define SAMPLES**. For example:

or

```bash
git log -G"#define SAMPLES"
```


Searches for **changes** in **lines containing** a specific string or the string matching provided **REGEXP**. For example:

```bash
-#define SAMPLES 100000
+#define SAMPLES 100000000
```


* * *

Listing Contributions by Author
-------------------------------

**git shortlog** summarizes **git log** and groups by author.

If no parameters are given, a list of all commits made per committer will be shown in chronological order.

```bash
$ git shortlog
Committer 1 (<number_of_commits>):
 Commit Message 1
 Commit Message 2
  ...
Committer 2 (<number_of_commits>):
 Commit Message 1
 Commit Message 2
 ...
```


To simply see the number of commits and suppress the commit description, pass in the summary option:

```bash
`-s` / `--summary`
```

```bash
$ git shortlog -s
<number_of_commits> Committer 1
<number_of_commits> Committer 2
```

To sort the output by the number of commits instead of alphabetically by committer name, pass in the numbered option:


```bash
`-n` / `--numbered`
```
To add the email of a committer, add the email option:

```bash
`-e` / `--email`
```

A custom format option can also be provided if you want to display information other than the commit subject:

```bash
`--format`
```

This can be any string accepted by the **–format** option of **git log**.

See the **Colorizing Logs** above for more information on this.

* * *

Finding Specific Commits with Log Search
----------------------------------------

Searching git log using some string in the log:

```bash
git log [options] --grep "search_string"
```


Example:

```bash
git log --all --grep "removed file"
```


Will search for the removed **file** string in all **logs** in all **branches**.

Starting from **git 2.4+**, the search can be inverted using the **--invert-grep** option.

Example:

```bash
git log --grep="add file" --invert-grep
```


Will show all commits that do not contain an add **file**.

* * *

Viewing Logs for Specific Lines in a File
-----------------------------------------

```bash
$ git log -L 1,20:index.html

commit 6a57fde739de66293231f6204cbd8b2feca3a869
Author: John Doe <john@doe.com>
Date: Tue Mar 22 16:33:42 2016 -0500

  commit message

diff --git a/index.html b/index.html
--- a/index.html
+++ b/index.html
@@ -1,17 +1,20 @@
  <!DOCTYPE HTML>
  <html>
-    <head>
-    <meta charset="utf-8">
+
+<head>
+    <meta charset="utf-8">
     <meta http-equiv="X-UA-Compatible" content="IE=edge">
     <meta name="viewport" content="width=device-width, initial-scale=1">
```


* * *

Filtering Logs for Specific Criteria
------------------------------------

```bash
git log --after '3 days ago'
```


Specific dates work too:

```bash
git log --after 2024-05-01
```


As with other commands and flags that accept a date parameter, the allowed date format is supported by GNU date (highly flexible).

An alias to **--after** is **--since**

Flags exist for the converse too: **--before** and **--until**.

You can also filter logs by author. e.g.

* * *

Viewing Logs with Inline Changes
--------------------------------

To see the log with changes inline, use the **-p** or **--patch** options.

Example (from **Trello Scientist** repository)

```bash
ommit 8ea1452aca481a837d9504f1b2c77ad013367d25
Author: Raymond Chou <info@raychou.io>
Date: Wed Mar 2 10:35:25 2016 -0800
    
    fix readme error link
    
diff --git a/README.md b/README.md
index 1120a00..9bef0ce 100644
--- a/README.md
+++ b/README.md
@@ -134,7 +134,7 @@ the control function threw, but *after* testing the other functions and
readying
  the logging. The criteria for matching errors is based on the constructor and message.
-You can find this full example at examples/errors.js.
+You can find this full example at examples/errors.js.
## Asynchronous behaviors
commit d3178a22716cc35b6a2bdd679a7ec24bc8c63ffa
:
```


* * *

Displaying Committed Files in Logs
----------------------------------

Example:

```bash
commit 4ded994d7fc501451fa6e233361887a2365b91d1
Author: Manassés Souza <manasses.inatel@gmail.com>
Date: Mon Jun 6 21:32:30 2016 -0300
 
  MercadoLibre java-sdk dependency
 
  mltracking-poc/.gitignore | 1 +
  mltracking-poc/pom.xml | 14 ++++++++++++--
  2 files changed, 13 insertions(+), 2 deletions(-)

commit 506fff56190f75bc051248770fb0bcd976e3f9a5
Author: Manassés Souza <manasses.inatel@gmail.com>
Date: Sat Jun 4 12:35:16 2016 -0300

  [manasses] generated by SpringBoot initializr

.gitignore | 42
++++++++++++
 mltracking-poc/mvnw | 233
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 mltracking-poc/mvnw.cmd | 145
+++++++++++++++++++++++++++++++++++++++
 mltracking-poc/pom.xml | 74
++++++++++++++++++++
 mltracking-poc/src/main/java/br/com/mls/mltracking/MltrackingPocApplication.java | 12 ++++
 mltracking-poc/src/main/resources/application.properties | 0
 mltracking-poc/src/test/java/br/com/mls/mltracking/MltrackingPocApplicationTests.java | 18 +++++
7 files changed, 524 insertions(+)
```


* * *

Viewing the Contents of a Specific Commit
-----------------------------------------

Using **git show** we can view a single commit

or

```bash
git show 48c83b3690dfc7b0e622fd220f8f37c26a77c934
```


Example

```bash
commit 48c83b3690dfc7b0e622fd220f8f37c26a77c934
Author: Matt Clark <mrclark32493@gmail.com>
Date: Wed May 4 18:26:40 2016 -0400
  
  The commit message will be shown here.

diff --git a/src/main/java/org/jdm/api/jenkins/BuildStatus.java
b/src/main/java/org/jdm/api/jenkins/BuildStatus.java
index 0b57e4a..fa8e6a5 100755
--- a/src/main/java/org/jdm/api/jenkins/BuildStatus.java
+++ b/src/main/java/org/jdm/api/jenkins/BuildStatus.java
@@ -50,7 +50,7 @@ public enum BuildStatus {
     colorMap.put(BuildStatus.UNSTABLE, Color.decode( "#FFFF55" ));
-    colorMap.put(BuildStatus.SUCCESS, Color.decode( "#55FF55" ));
+    colorMap.put(BuildStatus.SUCCESS, Color.decode( "#33CC33" ));
     colorMap.put(BuildStatus.BUILDING, Color.decode( "#5555FF" ));
```


* * *

Comparing Logs Between Two Branches
-----------------------------------

**git log master..foo** will show the commits that are on foo and not on master. Helpful for seeing what commits you’ve added since branching!

* * *

Showing Commits with Author Name and Time Since Commit
------------------------------------------------------

```bash
tree = log --oneline --decorate --source --pretty=format:'"%Cblue %h %Cgreen %ar %Cblue %an %C(yellow) %d %Creset %s"' --all --graph
```


example

```bash
* 40554ac 3 months ago Alexander Zolotov Merge pull request #95 from
gmandnepr/external_plugins
|\
| * e509f61 3 months ago Ievgen Degtiarenko Documenting new property
| * 46d4cb6 3 months ago Ievgen Degtiarenko Running idea with external plugins
| * 6253da4 3 months ago Ievgen Degtiarenko Resolve external plugin classes
| * 9fdb4e7 3 months ago Ievgen Degtiarenko Keep original artifact name as this may be
important for intellij
| * 22e82e4 3 months ago Ievgen Degtiarenko Declaring external plugin in intellij section
|/
* bc3d2cb 3 months ago Alexander Zolotov Ignore DTD in plugin.xml
```


* * *

Conclusion
----------

So this is all about Git Log and their ways of logging. In an upcoming article, we will deep dive into Git Remote Branch.