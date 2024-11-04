---
title: "Master Git Remotes: How to Manage, Update, and Sync Your Repositories"
excerpt: "Learn how to manage Git remotes effectively with this comprehensive guide. This article covers everything you need to know about working with Git remotes, from adding and removing remotes to syncing with upstream repositories."
date: Aug 16, 2024
layout: post
author: neha
categories:
    - git
image: assets/techalgospotlight-git-banner.webp
keywords: git remotes, git remote add, git remote remove, git remote update, git push, git pull, git fetch, git remote issues
published: true
---

When working with Git, understanding how to manage remotes is crucial for maintaining a smooth and efficient workflow. Whether you’re collaborating on a large project or just syncing your local code with a repository, mastering remote operations can save you time and prevent common issues.

This guide covers everything you need to know about working with **Git remotes**, from removing outdated branches to setting up new repositories. By the end, you’ll be well-equipped to handle any remote operation with confidence, keeping your codebase clean and your projects on track. Let’s dive in!

* * *

How to Remove a Remote Branch in Git
------------------------------------

To delete a remote branch in Git:

```bash
git push [remote-name] --delete [branch-name]
```

or

```bash
git push [remote-name] :[branch-name]
```

* * *

Updating Your Git Remote URL
----------------------------

Check existing remote

```bash
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
```


Changing repository URL

```bash
git remote set-url origin https://github.com/username/repo2.git
# Change the 'origin' remote's URL
```


Verify new remote URL

```bash
git remote -v
# origin https://github.com/username/repo2.git (fetch)
# origin https://github.com/username/repo2.git (push)
```


* * *

Viewing Your Current Git Remotes
--------------------------------

List all the existing remotes associated with this repository:

List all the existing remotes associated with this repository in detail including the fetch and push URLs:

or simply

* * *

Cleaning Up Local Copies of Deleted Remote Branches
---------------------------------------------------

If a remote branch has been deleted, your local repository has to be told to prune the reference to it.

To prune deleted branches from a specific remote:

```bash
git fetch [remote-name] --prune
```


To prune deleted branches from all remotes:

* * *

Syncing with an Upstream Repository
-----------------------------------

Assuming you set the upstream (as in the “setting an upstream repository”)

```bash
git fetch remote-name
git merge remote-name/branch-name
```


The pull command combines a fetch and a merge.

The pull with **--rebase** flag command combines a **fetch** and a **rebase** instead of merge.

```bash
git pull --rebase remote-name branch-name
```


* * *

**Using git ls-remote to List Remote References**
---------------------------------------------------

**git ls-remote** is one unique command allowing you to query a remote repo without having to clone/fetch it first.

It will list refs/heads and refs/tags of said remote repo.

You will see sometimes refs/tags/v0.1.6 and refs/tags/v0.1.6^{}: the ^{} to list the dereferenced annotated  
tag (ie the commit that the tag is pointing to)

Since git 2.8 (March 2016), you can avoid that double entry for a tag, and list directly those dereferenced tags with:

It can also help resolve the actual URL used by a remote repo when you have **"url.<base>.insteadOf"** config setting. If **git remote --get-url** returns **https://server.com/user/repo**, and you have set **git config url.ssh://git@server.com:**. instead of **https://server.com/:**

```bash
git ls-remote --get-url <aremotename>
ssh://git@server.com:user/repo
```


* * *

New Remote Repository in Git
----------------------------

```bash
git remote add upstream git-repository-url
```


Adds remote git repository represented by **git-repository-url** as a new remote named upstream to the git repository

* * *

Setting Upstream Branches for New Git Branches
----------------------------------------------

You can create a new branch and switch to it using

After you use git checkout to create a new branch, you will need to set that upstream origin to push to using

```bash
git push --set-upstream origin AP-57
```


After that, you can use git push while you are on that branch.

* * *

Push to the Remote Branch
-------------------------

Syntax for pushing to a remote branch

```bash
git push <remote_name> <branch_name>
```


Example

* * *

How to Rename a Git Remote
--------------------------

To rename the remote, use the command **git remote rename**

The **git remote rename** the command takes two arguments:

*   An existing remote name, for example: **origin**
*   A new name for the remote, for example: **destination**

Get the existing remote name

Check existing remote with URL

```bash
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
```


Rename remote

```bash
git remote rename origin destination
# Change remote name from 'origin' to 'destination'
```


Verify new name

```bash
git remote -v
# destination https://github.com/username/repo.git (fetch)
# destination https://github.com/usernam/repo.git (push)
```


* * *

Displaying Detailed Information About a Specific Git Remote
-----------------------------------------------------------

Output some information about a known remote: **origin**

Print just the remote’s URL:

```bash
git config --get remote.origin.url
```


With 2.7+, it is also possible to do, which is arguably better than the above one that uses the config command.

```bash
git remote get-url origin
```


* * *

Setting the URL for a Specific Git Remote
-----------------------------------------

You can change the url of an existing remote by the command

```bash
git remote set-url remote-name url
```


* * *

Retrieving the URL of a Specific Git Remote
-------------------------------------------

You can obtain the url for an existing remote by using the command

```bash
git remote get-url <name>
```


By default, this will be

```bash
git remote get-url origin
```


* * *

How to Change Your Git Remote Repository
----------------------------------------

To change the URL of the repository you want your remote to point to, you can use the **set-url** option, like so:

```bash
git remote set-url <remote_name> <remote_repository_url>
```


Example:

```bash
git remote set-url heroku https://git.heroku.com/fictional-remote-repository.git
```


* * *

Conclusion
----------

So this is all about the Remote Repository in Git. In an upcoming article, we will deep dive into Git Staging.