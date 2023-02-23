---
layout: page
title: "Managing Remote Branches from the Command Line"
order: 17
session: 3
length: 10
toc: true
adapted: false
---

## Learning objectives

By the end of this episode, you will be able to create and manage branches in a
remote repository just by using Git at the command line. This is particularly
relevant if you are not using a platform like GitHub to host your remote
repository. You will also know how to use feature branching in this context.


## Creating a new remote branch from a local one

In the [Remote Branches with GitHub]({{ site.url }}/14_remote_branches_with_github/index.html)
episode, we looked at how to work with remote branches by creating them in a
remote repository hosted on GitHub. However, you may find yourself in a
situation where you aren't using GitHub or a similar platform: for example,
perhaps you are working with a remote repository on a departmental server. In
this episode we will summarise how you can create remote branches and work
with them just using Git. 

Suppose we're on a local branch `<local-branch>` and we want to create a
corresponding remote branch. The general way to do this is as follows:

1. Checkout the local branch `<local-branch>`.

2. Run the following command: 
   ```
   git push --set-upstream origin <local-branch>
   ```

This will create an upstream branch in the remote repository with the same name as
the local branch. A reference to the remote branch will also be created in the
local repository, denoted by the prefix `remotes/origin/` (or just `origin/`).
The local branch is set up to track the new remote branch, so that using
`git push` and `git pull` on the local branch will push commits to / pull
commits from the remote branch.


## Using feature branching

In the absence of using GitHub to merge a remote branch into another (via a
Pull Request), we need to perform merging locally and then push the results
up to the remote repository. This slightly alters the way we collaborate with
feature branching, specifically the protocol for merging feature branches back
into `main` found in the
[Collaborating with Branches]({{ site.url }}/15_collaborating_with_branches/index.html#protocol-for-merging-feature-branches-into-main)
episode.

Below we give steps for merging a feature branch `foo-feature` into `main`. We
assume `foo-feature` exists both as a remote branch in the remote repository and
also a local tracking branch in our local repository.

1. (Optional, but recommended): Push all changes from the local `foo-feature`
   to the upstream branch.

2. Pull any changes to `main` from the remote repository into your local version
   of `main` (using `git pull` on your local `main` branch). 

   a) If `main` was unchanged by the pull then go to step 2,
      otherwise go to step b) below.

   b) If `main` got updated by the pull, then merge `main` into `foo-feature`
      in your local repository before continuing, by using `git merge`.
      If there are merge conflicts, these MUST be resolved and the merge into
      `foo-feature` completed before continuing to step c) below. Take the
      opportunity to make sure this merge hasn't introduced any problems into
      the codebase (e.g. inconsistencies in naming, etc.)
   
   c) Pull the remote `main` into your local `main` again to be
      sure no further changes were made while you were performing the merge in
      step b). If the branch wasn't updated then proceed
      to step 2 below, otherwise curse your luck and go back to step b).

2. (Optional, but recommended): Push the commits in your local `foo-feature`
   branch to the corresponding remote branch.

3. Merge the `foo-feature` branch into `main` locally.

4. Push the changes to `main` from your local repository to the remote repository.


As an optional, but recommended clean up step: delete the remote branch
`foo-feature` from the remote repository (see below), delete the local
`origin/foo-feature` reference and, finally, delete the local `foo-feature` branch.


## Deleting remote branches

In order to delete a remote branch `origin/<branch>` with Git, run the following
command. 

```
git push --delete origin <branch>
```

Note that if you have a local branch `<branch>` for which `origin/<branch>`
was the upstream, then this won't delete the local branch. To delete the local
branch as well, use `git branch -d` as discussed in the episode
[Remote Branches with GitHub]({{ site.url }}/14_remote_branches_with_github/index.html#deleting-branches-from-a-local-repository).
