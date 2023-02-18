---
layout: page
title: "Collaborating with Branches"
order: 15
session: 2
length: 20
toc: true
adapted: false
---

## Learning objectives

TODO


## Collaborating with others and branch organisation

TODO:
* Contrast collaboration with working solo: there is one common repository, but
  now multiple associated local repositories: one for each developer.
* Stress the importance of needing to keep updated with each other's work, and
  to push your own changes promptly.

TODO:
* High level overview of a basic branching strategy: feature branches off of
  `main`.
* Why this is helpful: controlled merging of work, allows multiple people to
  work simultaneously without excessive communication.
* Need for merging `main` into feature branches as it gets updated by others.


## Example: Joe Bloggs and Jane Doe

We're now going to assume that Joe Bloggs and Jane Doe are two people collaborating
on the `git-good-practice` repository. They will work with the same
remote repository, created under Joe's account, but will each have their own
associated local repositories. They're going to use the _feature branch_
strategy, discussed in the previous section, to add:

* An entry to the cheatsheet about FOO.

* A new file documenting good practice when collaborating together.


In order for two people to work on the same remote repository on GitHub, they
each need to be listed as collaborators on the repository. If you are the
repository's owner, you can invite collaborators as follows:

TODO: instructions for inviting someone to collaborate on a repository on GitHub.


### Exercise

At this point in the course, we encourage participants to pair up and work
together on a common repository, taking the roles of Joe and Jane.

So, find a partner to work with. Have one of you invite the other as a collaborator
on your repository. The collaborator should then clone the other person's
repository using the above instructions, so that you are both working on a
common remote repository. In what follows, one of you should play the role of
Joe Bloggs and the other of Jane Doe.


> #### Solo work
> 
> If you are working through these course notes by yourself then try imagining
> you are two different developers collaborating on the repository together. We
> suggest you clone a fresh copy of the remote repository to a new local repository
> on your computer, while keeping your original local repository. This will
> help you simulate the scenario of collaborators each having their own local
> repository.


## Creating a remote branch on GitHub

Joe and Jane will be creating remote branches on GitHub and then creating
local versions to use for their work. Although not essential, this will allow
them to be able to see each other's work.

TODO: instructions for creating a branch on GitHub

Joe creates a remote branch called `FOO-work`, which will contain work on FOO.
Jane creates a remote branch called `collaboration-good-practice`, which will
contain work on good practice while collaborating. They create these remote
branches at the same time.


## Creating local branches that track remote ones

Having created the remote branches, Joe and Jane need to each create a local branch
that will track their remote branches. This can be done by running `git fetch`
followed by checking out a new local branch with the same name as the remote
branch. This is easiest seen by example. First, Joe runs the following command: in
the his local `git-good-practice` repository:

```
$ git fetch origin
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
From https://github.com/jbloggs9999/git-good-practice
 * [new branch]      Foo-work   -> origin/Foo-work
 * [new branch]      collaboration-good-practice -> origin/collaboration-good-practice
```

We won't go into detail about exactly what `git fetch origin` is doing. For
our purposes, we use it to inspect the remote repository for information about
any new branches, or commits that have been made in remote branches, that our
local repository doesn't yet know about. In Joe's case, the fetch reports
that there is are two new remote branches called `Foo-work` and
`collaboration-good-practice`, which are the branches Joe and Jane created on
GitHub a moment ago. If Joe lists out all
his branches, he'll find that he now has references to these new remote
branches in his local repository:

```
$ git branch --all
  branches-material
* main
  remotes/origin/Foo-work
  remotes/origin/HEAD -> origin/main
  remotes/origin/collaboration-good-practice
  remotes/origin/main
```

However, in order to work on FOO, Joe needs to create a local version of the remote
`Foo-work` branch where he can add commits and that tracks the remote
`origin/Foo-work` branch. This can be arranged by performing the following checkout:

```
$ git checkout FOO-work 
Switched to a new branch 'FOO-work'
branch 'FOO-work' set up to track 'origin/FOO-work'. 
```

You may be surprised by this: after all, we've asked Git to checkout a branch
that doesn't actually exist! Fortunately, Git is smart enough to realise that
what we want to do is set up a new local branch that tracks the `origin/Foo-work`
remote branch. So it automatically creates a new local branch — called `Foo-work` — that
will track `origin/Foo-work`, and checks out this new local branch for us. We
can verify this by listing all the branches again:

```
$ git branch --all
* Foo-work
  branches-material
  main
  remotes/origin/Foo-work
  remotes/origin/HEAD -> origin/main
  remotes/origin/collaboration-good-practice
  remotes/origin/main
```

Jane runs the analogous commands in her local repository:

```
$ git fetch origin
Username for 'https://github.com': janedoe9999
Password for 'https://janedoe9999@github.com':
From https://github.com/jbloggs9999/git-good-practice
 * [new branch]      Foo-work   -> origin/Foo-work
 * [new branch]      collaboration-good-practice -> origin/collaboration-good-practice

$ git checkout collaboration-good-practice 
Switched to a new branch 'collaboration-good-practice'
branch 'collaboration-good-practice' set up to track 'origin/collaboration-good-practice'.
```

## Working on the feature branches

### Joe Bloggs and his `Foo-work` feature branch

Joe adds the following content to `Git-cheatsheet.md`:

```
FOO

```

He then commits it on his (local) `Foo-work` branch:

```
$ git add Git-cheatsheet.md 

$ git commit -m "Add FOO"
[Foo-work 5d69bbb] Add FOO
 1 file changed, 2 insertions(+)
```

Checking the status, Joe confirms that his local `Foo-work` branch is 1 commit
ahead of the associated remote branch:

```
$ git status
On branch Foo-work
Your branch is ahead of 'origin/Foo-work' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

In order to back up his work and give Jane a preview of what he's been doing,
Joe pushes the changes to his local `Foo-work` branch to the remote
`origin/Foo-work`:

```
$ git push origin
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 309 bytes | 309.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/jbloggs9999/git-good-practice.git
   42a9a32..5d69bbb  Foo-work -> Foo-work
```

The history on Joe's `Foo-work` branch now looks like this:

```
$ git log --oneline -5
5d69bbb (HEAD -> Foo-work, origin/Foo-work) Add FOO
42a9a32 (origin/main, origin/collaboration-good-practice, origin/HEAD) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
5cf8321 Remove rubbish.txt
```


### Jane Doe and her `collaboration-good-practice` feature branch

Jane creates a new file called `Collaboration-good-practice.md` in the
`Good-practice-guides` directory (which she includes as a stand-alone commit)
and adds the following content about the above feature branch strategy:

```
# Best practice for collaboration

## A basic feature branch strategy

A basic way to collaborate on a common repository is to use *feature branching*.
New software 'features' (which could consist of bug fixes), are worked on in
their own dedicated branches that branch off the `main` branch and then are
merged back into `main` when the new 'feature' is ready to be shared with others.

```

Like Joe, she then also pushes the new commits on her local
`collaboration-good-practice` to the associated remote branch,
`origin/collaboration-good-practice`:

```
$ git push origin
Username for 'https://github.com': janedoe9999
Password for 'https://janedoe9999@github.com':
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 990 bytes | 990.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/jbloggs9999/git-good-practice.git
   42a9a32..fb535ee  collaboration-good-practice -> collaboration-good-practice
```

Having done this, her `collaboration-good-practice` history looks as follows:

```
$ git log --oneline -5
fb535ee (HEAD -> collaboration-good-practice, origin/collaboration-good-practice) Add material on feature branching
8867731 Start good practice guide on collaboration
42a9a32 (origin/main, origin/Foo-work, origin/HEAD) Ignore TODO list file
0984d2b Add material on basic pathspec usage (directories)
92b2ac2 Create general good practice guides directory
```

TODO: point out that `origin/collaboration-good-practice` hasn't been updated
in Joe's local repository and `origin/Foo-work` hasn't been updated in Jane's,
because they haven't fetched from the remote repository. This underlines the
fact that the information in local repositories about remote branches only
gets updated when you tell Git to do it by `git fetch` or `git pull`.


## Merging 

## First to the pass: Joe

Joe finishes his work before Jane does and so gets to work on merging his
feature branch into the `main` branch. But first he checks that Jane hasn't
merged any work into the remote `main` branch, by checking out `main` and
pulling in any changes from the remote:

```
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

$ git pull origin
Already up to date.
```

TODO: stress that just because we see `Your branch is up to date with 'origin/main'.`
doesn't mean that there aren't changes on the remote to pull in.

Since his `main` branch is fully up to date with the remote version, he can go
ahead and perform the merge of his feature branch into `main`:

```
$ git merge Foo-work 
TODO: fill in
```

In order to share his work with Jane, he immediately pushes the recent changes
to `main` to the remote repository:

```
$ git push origin
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 349 bytes | 349.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/jbloggs9999/git-good-practice.git
   d2b60ff..eb0e845  main -> main
```


### Jane: merging after changes to `main`

Jane is ready to merge her `collaboration-good-practice` feature branch into
`main`. However, she first checks that her local `main` branch is up-to-date
with the remote repository:

```
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

$ git pull origin
TODO: fill in
```

Jane finds that there have been changes made to the `main` branch while she
was working on her feature branch. Therefore, she merges her now updated (local)
`main` branch into her feature branch, to ensure her feature branch includes
the latest changes. She also then pushes her updated feature branch to the
remote repository, so that her local and remote branches are in-sync.

```
$ git checkout collaboration-good-practice 
Switched to branch 'collaboration-good-practice'
Your branch is up to date with 'origin/collaboration-good-practice'.

$ git merge main
TODO: fill in

$ git push origin
TODO: fill in
```

Having done this, she now effectively starts the protocol for merging a feature
branch into `main` again. First she checks there haven't been any further updates
to `main`:

```
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

$ git pull origin
Already up to date.
```

Having seen there are no further updates, she goes ahead and merges her
`collaboration-good-practice` feature branch into `main`. Then she pushes the
new changes to `main` to the remote repository:

```
$ git merge collaboration-good-practice 
TODO: fill in

$ git push origin
TODO: fill in
```

Jane now views the history of all the branches. She does this by using the
`--all` option to show all branches, and then also the `--graph` option to
pictorially represent the inter-relationships of the branches:

```
$ git log --oneline --all --graph
TODO: fill in
```