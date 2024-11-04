---
title: ".gitignore File: How to ignore files and folders"
excerpt: "Learn how to create a .gitignore file to ignore files and folders in your Git repository. This guide covers the syntax and usage of .gitignore, and how to exclude files from version control."
date: Aug 18, 2024
layout: post
author: neha
categories:
    - git
image: assets/techalgospotlight-git-banner.webp
keywords: git ignore files, git ignore folders, git ignore patterns, git exclude files
published: true
---

A .gitignore file is used to ignore files and folders in the project directory. When one developer shares code with another, there are files that you don’t need to share. Examples are temp files, personal files, env files, log files etc.

This topic illustrates how to avoid adding unwanted files (or file changes) in a Git repo. There are several ways (global or local **.gitignore , .git/exclude , git update-index --assume-unchanged**, and **git update-index -- skip-tree**), but keep in mind Git is managing content, which means: ignoring actually ignores a folder content (i.e. files). An empty folder would be ignored by default since it cannot be added anyway.

* * *

Let’s see, How we can ignore files and directories
--------------------------------------------------

You can make Git ignore certain files and directories — that is, exclude them from being tracked by Git — by creating one or more **.gitignore** files in your repository.

In software projects, .gitignore typically contains a listing of files and/or directories that are generated during the build process or at runtime. Entries in the .gitignore file may include names or paths pointing to

*   temporary resources e.g. caches, log files, compiled code, etc.
*   local configuration files that should not be shared with other developers
*   files containing secret information, such as login passwords, keys and credentials

When created in the top-level directory, the rules will apply recursively to all files and sub-directories throughout the entire repository. When created in a sub-directory, the rules will apply to that specific directory and its sub-directories.

When a file or directory is ignored, it will not be:

*   tracked by Git
*   reported by commands such as **git status** or **git diff**
*   staged with commands such as **git add -A**

In the unusual case that you need to ignore tracked files, special care should be taken. See: Ignore files that have already been committed to a Git repository.

* * *

Git Ignore File Examples
------------------------

Here are some generic examples of rules in a .gitignore file, based on **glob file patterns)**:

```bash
# Lines starting with `#` are comments.

# Ignore files called 'file.ext'
file.ext

# Comments can't be on the same line as rules!
# The following line ignores files called 'file.ext # not a comment' 
file.ext # not a comment

# Ignoring files with full path.
# This matches files in the root directory and subdirectories too. 
# i.e. otherfile.ext will be ignored anywhere on the tree. 
dir/otherdir/file.ext
otherfile.ext

# Ignoring directories
# Both the directory itself and its contents will be ignored. 
bin/
gen/

# Glob pattern can also be used here to ignore paths with certain characters.
# For example, the below rule will match both build/ and Build/
[bB]uild/

# Without the trailing slash, the rule will match a file and/or
# a directory, so the following would ignore both a file named `gen`
# and a directory named `gen`, as well as any contents of that directory 
bin
gen

# Ignoring files by extension
# All files with these extensions will be ignored in # this directory and all its sub-directories.
*.apk
*.class

# It's possible to combine both forms to ignore files with certain 
# extensions in certain directories. The following rules would be 
# redundant with generic rules defined above.
java/*.apk
gen/*.class

# To ignore files only at the top level directory, but not in its # subdirectories, prefix the rule with a `/`
/*.apk
/*.class

# To ignore any directories named DirectoryA
# in any depth use ** before DirectoryA
# Do not forget the last /,
# Otherwise it will ignore all files named DirectoryA, rather than directories 
**/DirectoryA/
# This would ignore
# DirectoryA/
# DirectoryB/DirectoryA/
# DirectoryC/DirectoryB/DirectoryA/
# It would not ignore a file named DirectoryA, at any level

# To ignore any directory named DirectoryB within a
# directory named DirectoryA with any number of
# directories in between, use ** between the directories 
DirectoryA/**/DirectoryB/
# This would ignore
# DirectoryA/DirectoryB/
# DirectoryA/DirectoryQ/DirectoryB/
# DirectoryA/DirectoryQ/DirectoryW/DirectoryB/

# To ignore a set of files, wildcards can be used, as can be seen above.
# A sole '*' will ignore everything in your folder, including your .gitignore file. 
# To exclude specific files when using wildcards, negate them.
# So they are excluded from the ignore list:
!.gitignore

# Use the backslash as escape character to ignore files with a hash (#) 
# (supported since 1.6.2.1)
\#*#
```


Most **.gitignore** files are standard across various languages, so to get started, here is a set of sample .gitignore files listed by language from which to clone or copy/modify into your project. Alternatively, for a fresh project, you may consider auto-generating a starter file using an **online tool**.

### Other forms of .gitignore

**.gitignore** files are intended to be committed as part of the repository. If you want to ignore certain files without committing the ignore rules, here are some options:

*   Edit the **.git/info/exclude** file (using the same syntax as **.gitignore**). The rules will be global in the scope of the repository;
*   Set up a global gitignore file that will apply ignore rules to all your local repositories:

Furthermore, you can ignore local changes to tracked files without changing the global git configuration with:

*   **git update-index --skip-worktree […]**: for minor local modifications
*   **git update-index --assume-unchanged […]**: for production-ready, non-changing files upstream

See **more details on the differences between the latter flags** and the **git update-index** documentation for further options.

### Cleaning up ignored files

You can use **git clean -X** to clean up ignored files:

```bash
git clean -Xn #display a list of ignored files
git clean -Xf #remove the previously displayed files
```


Note: -X (caps) cleans up only ignored files. Use -x (no caps) to also remove untracked files.

See the **git clean** documentation for more details.

* * *

How git check file is ignored or not
------------------------------------

The **git check-ignore** command reports on files ignored by Git.

You can pass filenames on the command line and **git check-ignore** will list the filenames that are ignored. For example:

```bash
$ cat .gitignore
*.o
$ git check-ignore example.o Readme.md 
example.o
```


Here, only \*.o files are defined in .gitignore, so Readme.md is not listed in the output of **git check-ignore**.

If you want to see a line of which .gitignore is responsible for ignoring a file, add -v to the git check-ignore command:

```bash
$ git check-ignore -v example.o Readme.md 
.gitignore:1:*.o       example.o
```


From Git 1.7.6 onwards you can also use **git status --ignored** to see ignored files. You can find more info on this in the **official documentation** or in Finding files ignored by .gitignore.

* * *

Git Exceptions in a .gitignore file
-----------------------------------

If you ignore files by using a pattern but have exceptions, prefix an exclamation mark(!) to the exception. For example:

The above example instructs Git to ignore all files with the **.txt** extension except for files named important**.txt**.

If the file is in an ignored folder, you can **NOT** re-include it so easily:

In this example, all .txt files in the folder would remain ignored.

The right way is to re-include the folder itself on a separate line, then ignore all files in a folder by \*, and finally re-include the \*.txt in a folder, as the following:

```bash
!folder/ 
folder/* 
!folder/*.txt
```


> **Note**: For file names beginning with an exclamation mark, add two exclamation marks or escape with the \\ character:

```bash
!!includethis 
\!excludethis
```


* * *

Git global .gitignore file
--------------------------

To have Git ignore certain files across all repositories you can **create a global .gitignore** with the following command in your terminal or command prompt:

```bash
$ git config --global core.excludesfile <Path_To_Global_gitignore_file>
```


Git will now use this in addition to each repository’s .gitignore file. Rules for this are:

*   If the local .gitignore file explicitly includes a file while the global .gitignore ignores it, the local .gitignore takes priority (the file will be included)
*   If the repository is cloned on multiple machines, then the global .gigignore must be loaded on all machines or at least include it, as the ignored files will be pushed up to the repo while the PC with the global .gitignore wouldn’t update it. This is why a repo-specific .gitignore is a better idea than a global one if the project is worked on by a team.

This file is a good place to keep platform, machine or user-specific ignores, e.g. **OSX.DS\_Store**, Windows **Thumbs.db** or **Vim \*.ext~** and **\*.ext.swp** ignores if you don’t want to keep those in the repository. So one team member working on OS X can add all **.DS\_STORE** and \_MACOSX (which is useless), while another team member on Windows can ignore all **thumbs.bd**

* * *

Git ignore files that have already committed
--------------------------------------------

If you have already added a file to your Git repository and now want to **stop tracking** it (so that it won’t be present in future commits), you can remove it from the index:

This will remove the file from the repository and prevent further changes from being tracked by Git. The **--cached** option will make sure that the file is not physically deleted.

Note that previously added contents of the file will still be visible via the Git history.

Keep in mind that if anyone else pulls from the repository after you remove the file from the index, **their copy will be physically deleted.**

You can make Git pretend that the working directory version of the file is up to date and read the index version instead (thus ignoring changes in it) with “skip worktree” bit:

```bash
git update-index --skip-worktree <file>
```


Writing is not affected by this bit, content safety is still the priority. You will never lose your precious ignored changes; on the other hand, this bit conflicts with stashing: to remove this bit, use

```bash
git update-index --no-skip-worktree <file>
```


It is sometimes **wrongly** recommended to lie to Git and have it assume that file is unchanged without examining it. It looks at first glance as ignoring any further changes to the file, without removing it from its index:

```bash
git update-index --assume-unchanged <file>
```


This will force git to ignore any change made in the file (keep in mind that if you pull any changes to this file, or you stash it, **your ignored changes will be lost**)

If you want git to “care” about this file again, run the following command:

```bash
git update-index --no-assume-unchanged <file>
```


* * *

Git Ignoring a file in any directory
------------------------------------

To ignore a file foo.txt in **any** directory, you should just write its name:

```bash
foo.txt # matches all files 'foo.txt' in any directory
```


If you want to ignore the file only in part of the tree, you can specify the subdirectories of a specific directory with \*\* pattern:

```bash
bar/**/foo.txt # matches all files 'foo.txt' in 'bar' and all subdirectories
```


Or you can create a .gitignore file in the bar/ directory. Equivalent to the previous example would be creating file bar/.gitignore with these contents:

```bash
foo.txt # matches all files 'foo.txt' in any directory under bar/
```


* * *

Git Ignoring files in a subfolder
---------------------------------

Suppose you have a repository structure like this:

```bash
examples/ 
  output.log
src/
  <files not shown> 
  output.log
README.md
```


**output.log** in the examples directory is valid and required for the project to gather an understanding while the one beneath src/ is created while debugging and should not be in the history or part of the repository.

There are two ways to ignore this file. You can place an absolute path into the **.gitignore** file at the root of the working directory:

```bash
# /.gitignore
src/output.log
```


Alternatively, you can create a **.gitignore** file in the **src/** directory and ignore the file that is relative to this **.gitignore**:

```bash
# /src/.gitignore
output.log
```


* * *

Git finding files ignored by .gitignore
---------------------------------------

You can list all files ignored by git in the current directory with the command:

So if we have a repository structure like this:

```bash
.git
.gitignore 
./example_1 
./dir/example_2 
./example_2
```


…and .gitignore file containing:

…than result of the command will be:

```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed) 

.gitignore
.example_1

Ignored files:
  (use "git add -f <file>..." to include in what will be committed)
dir/ 
example_2
```


If you want to list recursively ignored files in directories, you have to use additional parameter – – untracked- files=all

The result will look like this:

```bash
$ git status --ignored --untracked-files=all 
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed) 

.gitignore
example_1

Ignored files:
  (use "git add -f <file>..." to include in what will be committed)
  
dir/example_2 
example_2
```


* * *

Git clears already committed files, but included in .gitignore
--------------------------------------------------------------

Sometimes it happens that a file was being tracked by git, but in a later point in time was added to .gitignore, to stop tracking it. It’s a very common scenario to forget to clean up such files before its addition to .gitignore. In this case, the old file will still be hanging around in the repository.

To fix this problem, one could perform a “dry-run” removal of everything in the repository, followed by re-adding all the files back. As long as you don’t have pending changes and the –cached parameter is passed, this command is fairly safe to run:

```bash
# Remove everything from the index (the files will stay in the file system)
$ git rm -r --cached .

# Re-add everything (they'll be added in the current state, changes included)
$ git add .

# Commit, if anything changed. You should see only deletions
$ git commit -m 'Remove all files that are in the .gitignore'

# Update the remote
$ git push origin master
```