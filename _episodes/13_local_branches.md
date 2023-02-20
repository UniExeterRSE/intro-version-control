---
layout: page
title: "Working with Local Branches"
order: 13
session: 2
length: 20
toc: true
adapted: false
---

## Learning objectives

At the end of this episode you will be able to explain what branches are and how you might use them. 
You will also be able to demonstrate how to create an experimental branch and merge it back into the `main` branch. 


## Concept of branches

TODO
* Idea as (1) a linear collection of commits, and (2) a pointer to a particular
  commit
* Why we want to use branches:
  - Organisational tool, to separate development of new features / bug fixes
    from a canonical 'latest' version of software
  - As an aid to collaboration (to be discussed later): different people work
    with different branches at the same time, merging as a way to combine work
    in a controlled way.


## Working with local branches

We're going to add some new content to the cheatsheet, doing this in a new, dedicated
branch. The content we'll add will be about using branches, so we'll be recording
what we learn as we go.


### Creating branches

The general way to create a new branch in our local repository is

```
git branch <new-branch-name>
```

where `<new-branch-name>` is the name of the branch we wish to work on.

TODO: explain this creates branch at the current commit i.e. `HEAD`.

> #### Branching off a commit
>
> TODO: explain how to start a branch at any commit.


In our example, we create a new branch
off of our most recent commit, called `branches-material`:

```
$ git branch branches-material
```

This will shortly be the branch in which we add new content to the cheatsheet.


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

> #### `main` is just a branch
>
> TODO: explain that `main` is a branch, one that is created for us by default
> to hold commits in a new repository.


### Adding commits to a branch

In order to work on a branch, we need to **checkout** the branch so that any
new commits we make are added to the branch. The general command for doing this
is:

```
git checkout <branch>
```

We now switch to our new branch `branches-material` so that
our new cheatsheet content will feature in this branch, rather than the branch
`main`:

```
$ git checkout branches-material 
Switched to branch 'branches-material'
```

We're now ready to get to work in the branch `branches-material`. We add the
following content to `Git-cheatsheet.md` on what we just learned about creating
a branch.

```

## Branches

`git branch <branch>` — Create a new local branch called `<branch>` based at the
                        current commit (i.e. at `HEAD`).

```

We make a commit with the new change:

```
$ git add Git-cheatsheet.md

$ git commit -m "Add entry about creating branches"
[branches-material 8124186] Add entry about creating branches
 1 file changed, 6 insertions(+)
```

We next add an entry to our cheatsheet about checking out a branch:

```
`git checkout <branch>` — Check out the branch `<branch>`, so that new commits
                          are added to `<branch>`.

```

Having committed this change, we now view the log to see our new commits:

```
$ git log --oneline -5
51da8da (HEAD -> branches-material) Add entry about checking out a branch
8124186 Add entry about creating branches
42a9a32 (origin/main, origin/HEAD, main) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
```

We can see that the new commits have been added to the branch `branches-material`.

TODO: explain log output:
* Confirmation that we are working on `branches-material` as indicated by
  `HEAD -> branches-material`.
* New commits on `branches-material` branch, but not on `main` because `main`
  stops at commit `42a9a32`.

We can verify that these new commits are not on the `main` branch by examining
the log of `main` directly. In general, we can run

```
git log [options] <branch>
```

to view the commit history contained in a specific branch `<branch>`, where
`[options]` are any optional arguments we want to include e.g `--oneline`. In
our example, we get the following history for the `main` branch:

```
$ git log --oneline -5 main
42a9a32 (origin/main, origin/HEAD, main) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
5cf8321 Remove rubbish.txt
d26a698 Add some rubbish to try out 'git rm'
```

This confirms that the new commits are not on the `main` branch.


## Merging branches

Let's now look at how we can incorporate the changes we've made in the
`branches-material` branch into our `main` branch. In Git parlance, we want
to **merge** the commit history in `branches-material` into the history of
the `main` branch.

TODO: give a higher-level, intuitive explanation of what merging is doing.


We do this with the `merge` command:

```
git merge <branch-to-bring-in>
```

Here, `<branch-to-merge-in>` is the name of the branch whose commits we want
to bring _into_ the branch we're currently on.

In our example, we need to merge the branch `branches-material` into `main`.
To do this, we need to checkout the branch we want to merge _into_, i.e.
`main`:

```
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

Now we can merge `branches-material` into `main`:

```
$ git merge branches-material 
Updating 42a9a32..51da8da
Fast-forward
 Git-cheatsheet.md | 9 +++++++++
 1 file changed, 9 insertions(+)
```

Let's take another look at the log of `main`:

```
$ git log --oneline -5
51da8da (HEAD -> main, branches-material) Add entry about checking out a branch
8124186 Add entry about creating branches
42a9a32 (origin/main, origin/HEAD) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
```

We can see that the commits from `branches-material` have been added to
`main`. In fact, Git has just moved `main` to now point to the same commit
as at the end of the `branches-material`, as seen by the line

```
51da8da (HEAD -> main, branches-material) Add entry about checking out a branch
```

Our `main` branch now has some commits that have not been pushed to the remote
repository, so we will now rectify that:

```
$ git push
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 765 bytes | 255.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (4/4), completed with 2 local objects.
To https://github.com/jbloggs9999/git-good-practice.git
   42a9a32..51da8da  main -> main
```


### Exercise

Add another commit to the `branches-material` branch about merging branches. 
You may wish to use the following text:

```
`git merge <branch-to-merge-in>` — Combine the commit history of `<branch-to-merge-in>`
                                   with that of the branch currently checked out.
                                   
```

Once you've done that, bring the changes into `main` by merging the branch
`branches-material` into `main`. Finally, push the new commits on `main` to the
remote repository.
