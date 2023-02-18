---
layout: page
title: "Branches – The Basics"
order: 13
session: 2
length: 20
toc: true
adapted: false
---

## Learning objectives

TODO


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


## Creating and checking out branches


The general way to create a new branch in our local repository is

```
git branch <new-branch-name>
```

TODO: explain this creates branch at the current commit i.e. `HEAD`

In order to work on a branch, we need to **checkout** the branch so that any
new commits we make are added to the branch. The general command for doing this
is:

```
git checkout <branch>
```

where `<branch>` is the name of the branch we wish to work on.

Let's add some content to the cheatsheet about branches, doing this in a new, dedicated
branch. First, we create a new branch
off of our most recent commit, called `branches-material`:

```
$ git branch branches-material
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
and switching branches.

```

## Branches

`git branch <new-branch-name>` — Create a new branch called `<new-branch-name>`
                                 based at the current commit (i.e. at `HEAD`).

```

We make a commit with the new change:

```
$ git add Git-cheatsheet.md

$ git commit -m "Add entry about creating branches"
[branches-material b55eb9e] Add entry about creating branches
 1 file changed, 6 insertions(+)
```

We next add some more content to our files. We'll add entries to our cheatsheet
about pulling changes from a remote repository:

```
`git checkout <branch>` — Check out the branch `<branch>`, so that new commits
                          are added to `<branch>`.

```

Having committed this change, we now view the log to see our new commits:

```
$ git log --oneline -5
d2b60ff (HEAD -> branches-material) Add entry about checking out a branch
b55eb9e Add entry about creating branches
42a9a32 (origin/main, origin/HEAD, main) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
```
We can see that the new commit has been added to the branch `branches-material`.

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


## Merging branches - mechanics

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
Updating 42a9a32..d2b60ff
Fast-forward
 Git-cheatsheet.md | 9 +++++++++
 1 file changed, 9 insertions(+)
```

Let's take another look at the log of `main`:

```
$ git log --oneline -5
d2b60ff (HEAD -> main, branches-material) Add entry about checking out a branch
b55eb9e Add entry about creating branches
42a9a32 (origin/main, origin/HEAD) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
```

We can see that the commits from `branches-material` have been added to
`main`. In fact, Git has just moved `main` to now point to the same commit
as at the end of the `branches-material`, as seen by the line

```
d2b60ff (HEAD -> main, branches-material) Add entry about checking out a branch
```


### Exercise

TODO: add commit to `branches-material` branch about merging branches (provide
sample text to help if they're struggling to give a description). Then merge
into `main`.