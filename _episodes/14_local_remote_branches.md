---
layout: page
title: "Local and Remote Branches"
order: 14
session: 2
length: 20
toc: true
adapted: false
---


## Local and remote branches

TODO:
* Explain the concept of both local branches and remote branches, just like
  how we have commits in a local repository and/or in a remote repository.
* Explain how our local repository keeps references to remote branches, giving
  them names starting with `remotes/origin/` (or just `origin/`). But these
  are not kept in sync with the remote branches automatically - we need to use
  `git fetch` to update them.
* Explain the concept of a local branch tracking a remote one


### Viewing branches

We can view all the local branches we have in our local repository by running:

```
git branch --list
```

(Equivalently, we could use the short form `-l` for `--list`.)

In our `git-good-practice` repository, this would show us:

```
$ git branch --list
  branches-material
* main
```

TODO: explain what `* main` means.

We can list _all_ the branches that our local repository is aware of (both
local branches and remote branches) by using `git branch --all` (or
just `git branch -a`):

```
$ git branch --all
  branches-material
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
``` 

TODO:
* Add a note to ignore the `remotes/origin/HEAD -> origin/main` bit, we don't
  need to know what it means.
* Explain that so far we've only created `branches-material` as a branch in our
  local repository — there is currently no remote counterpart.
* Give instructions to view branches on GitHub and verify that there is no
  branch on there called `branches-material`.


## Creating a new remote branch from a local one

Suppose we're on a local branch `<local-branch>` and we want to create a corresponding remote
branch. The general way to do this is as follows:

1. Checkout the local branch `<local-branch>`.

2. Run the following command: 
   ```
   git push --set-upstream origin <local-branch>
   ```

This will create a remote branch in the remote repository with the same name as
the local branch. A reference to the remote branch will also be created in the
local repository, denoted by the prefix `remotes/origin/` (or just `origin/`).

In our example, we create a remote version of the `branches-material` branch
by following through the steps above:

```
$ git checkout branches-material 
Switched to branch 'branches-material'

$ git push --set-upstream origin branches-material
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (9/9), 1.08 KiB | 1.08 MiB/s, done.
Total 9 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), completed with 2 local objects.
remote: 
remote: Create a pull request for 'branches-material' on GitHub by visiting:
remote:      https://github.com/jbloggs9999/git-good-practice/pull/new/branches-material
remote:
To https://github.com/jbloggs9999/git-good-practice.git
 * [new branch]      branches-material -> branches-material
branch 'branches-material' set up to track 'origin/branches-material'.
```

TODO: explain that this will have pushed all commits in local branch to the
remote one. Also explain what the last line about tracking means.

If we look again at our full list of branches, we can see there is now a reference
`remotes/origin/branches-material` to the remote branch we just created:

```
$ git branch --all
* branches-material
  main
  remotes/origin/HEAD -> origin/main
  remotes/origin/branches-material
  remotes/origin/main
```

Moreover, if we were to go the remote repository on GitHub, we would see the new
remote branch in the _Branches_ section of the repository.


## Pushing commits from a local branch to its remote counterpart

TODO: explain that we can push commits from a local branch to the remote branch
that it's tracking.

Let's add a new entry to the cheatsheet about viewing branches:

```

### Viewing branches

`git branch -l` — List out local branches.

`git branch -a` — List out local branches and (known) remote branches.

```

We commit the change to our `branches-material` branch and then view the status:

```
$ git add Git-cheatsheet.md

$ git commit -m "Add material on viewing branches"
[branches-material 40e34c5] Add material on viewing branches
 1 file changed, 6 insertions(+)

$ git status
On branch branches-material
Your branch is ahead of 'origin/branches-material' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

The status is telling us that the new commit has not yet been pushed to the
remote branch `origin/branches-material` that we're tracking. Note:

* If we went to the _Branches_ section of the remote repository on GitHub, we
  would not see this new commit on the remote `branches-material` branch.

* We can also see this in the log (notice how `branches-material` is on our last
  commit whereas `origin/branches-material` is still on the previous commit):

  ```
  $ git log --oneline -3
  40e34c5 (HEAD -> branches-material) Add material on viewing branches
  0e75e27 (origin/branches-material, main) Add entry about 'git merge'
  d2b60ff Add entry about checking out a branch
  ```

To update our remote branch with the new commits in our local branch, we just
use `git push` from the `branches-material` branch:

```
$ git push origin
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 407 bytes | 135.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/jbloggs9999/git-good-practice.git
   0e75e27..40e34c5  branches-material -> branches-material
```

Now the latest commit also features on the remote branch in the remote
repository on GitHub.


## The other way: starting with remote branches

So far, we've seen how to create a local branch and then 'push' it to the
remote repository to create an associated remote branch. However, it is possible
to go the other way: to create a branch in the remote repository, from which
you create a local branch that tracks the remote branch.

In GitHub, the following steps allow you to create a new remote branch:

TODO: steps for creating a branch on GitHub (note that we need to chose a
base branch to start the new branch on).

In our example `git-good-practice` repository, let's suppose we've created a
new remote branch called `remote-branches-material`, which is based on top of our
`branches-material` branch. Our local repository doesn't have any knowledge of
this new branch, as can be seen by listing the branches:

```
$ git branch -a
* branches-material
  main
  remotes/origin/HEAD -> origin/main
  remotes/origin/branches-material
  remotes/origin/main
```

We will use a local version of this new branch to
add some material to the cheatsheet relating to working with remote branches. In
order to do this, we need to do the following:

* Update our local repository from the remote repository, so that we have a
  reference to the newly created remote branch (i.e. to create
  `origin/remote-branches-material`).

* Create a local branch that is set up to track `origin/remote-branches-material`.

* Add new commits to the local branch, then push these to the associated
  remote branch.


### Fetch the remote branch

In order to update our local repository so that it has knowledge of the new
remote branch, we use the following command from within our local repository:

```
git fetch
```

(Like with `git push` and `git pull`, we can instead run `git fetch origin` to
be explicit about the reference to the remote repository.)
We won't go into too much detail about exactly what `git fetch origin` is doing. For
our purposes, we use it to inspect the remote repository for information about
any new branches, or commits that have been made in remote branches, that our
local repository doesn't yet know about.

In our example, after running `git fetch` in our `git-good-practice`
repository, we see that information about the new remote `remote-branches-material`
has been retrieved:

```
$ git fetch
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
From https://github.com/jbloggs9999/git-good-practice
 * [new branch]      remote-branches-material -> origin/remote-branches-material

$ git branch -a
* branches-material
  main
  remotes/origin/HEAD -> origin/main
  remotes/origin/branches-material
  remotes/origin/main
  remotes/origin/remote-branches-material
```

However, this has only created a reference to the remote branch, indicated
by `remotes/origin/remote-branches-material` in the above output. We still need
to create a _local_ branch that will track the remote branch. 


### Create a new tracking local branch

In order to create a local version of the
`origin/remote-branches-material` branch where we can add commits, we can
perform the following checkout:

```
$ git checkout remote-branches-material 
Switched to a new branch 'remote-branches-material'
branch 'remote-branches-material' set up to track 'origin/remote-branches-material'. 
```

You may be surprised by this: after all, we've asked Git to checkout a branch
that doesn't actually exist! Fortunately, Git is smart enough to realise that
what we want to do is set up a new local branch that tracks the `origin/remote-branches-material`
remote branch. So it automatically creates a new local branch — called `remote-branches-material` — that
will track `origin/remote-branches-material`, and checks out this new local branch for us. We
can verify this by listing all the branches again:

```
$ git branch -a
  branches-material
  main
* remote-branches-material
  remotes/origin/HEAD -> origin/main
  remotes/origin/branches-material
  remotes/origin/main
  remotes/origin/remote-branches-material
```

### Add content to the local branch and push

We are now set to add our new material to `Git-cheatsheet.md` about remote
branches. We modify the start of the subsection _Branches_ so that it now reads as
follows:

```
## Branches

`git branch <new-branch-name>` — Create a new branch called `<new-branch-name>`
                                 based at the current commit (i.e. at `HEAD`).

`git checkout <branch>` — Check out the branch `<branch>`, so that new commits
                          are added to `<branch>`.

- Can also be used to create and checkout a new local branch `<branch>` that
  tracks an existing remote branch `origin/<branch>`.

`git merge <branch-to-merge-in>` — Combine the commit history of `<branch-to-merge-in>`
                                   with that of the branch currently checked out.
```

Having included this addition, we commit to our local `remote-branches-material` branch.


> #### Markdown syntax
>
> Unordered lists are denoted by using a hyphen (`-`) or an asterisk (`*`),
> followed by a space, with the text in the list item following. Example:
> 
> ```
> - Foo
> - Bar
> - Baz
> ```
> renders as:
> - Foo
> - Bar
> - Baz
> 
> Text that flows over multiple lines in the source file, yet belongs to a single
> list item, should respect the indenting. For example:
> 
> ```
> * list entry with
>   
>   new line
> 
> * the quick brown fox jumps over the
>   lazy dog
> ```
> 
> renders as:
> 
> * list entry with
>   
>   new line
> 
> * the quick brown fox jumps over the
>   lazy dog

Our log on `remote-branches-material` now looks like this:

```
$ git log --oneline -3
bac5ae2 (HEAD -> remote-branches-material) Add note about creating tracking local branches
40e34c5 (origin/remote-branches-material, origin/branches-material, branches-material) Add material on viewing branches
0e75e27 (main) Add entry about 'git merge'
```

We're now in the position where our local branch
`remote-branches-material` is ahead of the remote branch
`origin/remote-branches-material` that it tracks. So let's push our changes
to update the remote branch with the commit we just made locally:

```
$ git push
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 447 bytes | 447.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/jbloggs9999/git-good-practice.git
   40e34c5..bac5ae2  remote-branches-material -> remote-branches-material
```

The last line of the `git push` message shows that we've updated the remote
branch.


## Cleaning up

We've done quite a bit of work in our branches, some of which hasn't been merged
into `main`. We'll clean up the state of our repository by

* merging our `remote-branches-material` branch into `main`;

* pushing our changes from `main` to the remote repository; and finally

* deleting the branches `branches-material` and `remote-branches-material`,
  including the remote version of `remote-branches-material`, since they no
  longer serve any purpose.


> ### Good practice: deleting old branches
>
> It is good practice to delete branches that are no longer required. This makes
> navigating a repository easier and makes it clear what work is still ongoing
> compared to work that has been finished.

First, we merge `remote-branches-material` into `main`:

```
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

$ git merge remote-branches-material
Updating 0e75e27..bac5ae2
Fast-forward
 Git-cheatsheet.md | 11 ++++++++++-
 1 file changed, 10 insertions(+), 1 deletion(-)
```

Next, we push our changes to `main`:

```
$ git checkout main
Already on 'main'
Your branch is ahead of 'origin/main' by 5 commits.
  (use "git push" to publish your local commits)

$ git push
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/jbloggs9999/git-good-practice.git
   42a9a32..bac5ae2  main -> main
```

Finally, we delete our non-main branches. The general commands for deleting
branches are as follows:

* For deleting _local_ branches: `git branch -d <local-branches>`

* For deleting _remote_ branches: `git branch -d -r <remote-branches>`

In both cases, note that you can specify more than one branch by separating the
branch names by a space.

There are a couple of important things to note about deleting branches:

* You can't delete a branch you currently have checked out. So make sure you
  checkout a different branch before deletion e.g. do deletions from `main`.

* Deleting branches removes the commits contained in those branches which don't
  feature in other branches. So, before deleting a branch, be sure that the
  changes you want to keep have been merged into another branch e.g. `main`.

We delete our local branches:

```
$ git branch -d branches-material remote-branches-material
Deleted branch branches-material (was 40e34c5).
Deleted branch remote-branches-material (was bac5ae2).
```

Then we delete our references to the remote branches:

TODO: may need to change this if e.g. branches-material is not a remote branch.

```
$ git branch -r -d origin/branches-material origin/remote-branches-material
Deleted remote-tracking branch origin/branches-material (was 40e34c5).
Deleted remote-tracking branch origin/remote-branches-material (was bac5ae2).
```

> ### Force deletion
> 
> Git may stop you from deleting a branch, because it can't verify that
> all the commits in the branch have been merged into a corresponding remote
> branch or another local branch. This is a protection
> mechanism to stop you from potentially losing changes. If you encounter this but
> are sure you want to proceed with the deletion, you can force the deletion
> by using `-D` instead of `-d` in the commands above.


Finally, we need to delete the remote branches from the remote repository in
GitHub.

TODO: instructions for deleting branches in GitHub.
