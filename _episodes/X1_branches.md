---
layout: page
title: "Creating and using branches for development"
order: 99
session: 2
length: 15
toc: false
adapted: false
---

## Learning objectives

Understand how to create branches within a GitHub repository
Re contextualise our understanding from session 1 with knowledge of branches
Be able to switch between branches

## Why work on branches

When you are working on an enhancement to an existing piece of software, it's rare that the work can be carried out without complications! It's often that case that your new code will break or clash with an existing aspect of your software, meaning that you need a safe, contained environment to test and debug your changes to the code base before they can be fully introduced.

** Github always works with branches - the first branch is named main and is made the default branch, but technically it is no different from any other kind of branch.
** All of the content from session 1 applies equally to working on a branch as it does to working on "main"

## What's in a branch?

* Github tracks changes relative to a base
* A branch is a clean set of changes relative to a particular commit.

## Creating a branch

First things first, we need to create a new branch. Let's list the current branch we are working on using the command:
```
$   git branch --show-current
```
This should return the name of the default branch, ```main```.
To create and switch to a new branch we use the following command:
```
$   git checkout -b test_branch
```
If we now check which branch we are currently working on, we can see that we have successfully created and switched to the new branch: 

```
$    git branch --show-current
test_branch
```

Lets create a new text file containing some new information. In order to add the new file we need to use ```git add``` (this was covered in episode 7) to stage the changes. Once the file has been staged, we can commit the file to the new branch.

> NOTE:
> It is also possible to create a new branch by simply using the command ```git branch new_branch``` and then manually switching to it. You can also use ```git switch -c new_branch```.

## Pushing the branch

If we look at the GitHub repository using a browser, we can see that our new branch hasn't appeared. That is because we have only created a local branch, which is only tracking changes that we are making on our own machine. In order to make this branch a "remote branch" of the repository, we need to push the branch to our remote repository:

```
$   git push --set-upstream origin
```

By using the option ```--set-upstream origin``` we are telling git to push the branch to the same repository that its parent branch was cut from.

## Switching between branches

Now we are free to work within our own workspace and follow the modify-add-commit pattern we outlined in session 1, whilst making sure to periodically push changes to the remote repository when ready. However, if we want to switch back to the origin branch again, we can easily do so.
First, we can make note of the available branches in the repository:

```
$   git branch -l
  list
  main
* test-branch
```

The asterisk indicates that we are currently working on the branch "test_branch" and we can see that our main branch is also available to switch to (Note that ```git branch -l``` is shorthand for ```git branch --list```). We can switch branches easily:

```
$   git switch main
$   git branch --show-current
main
```

## Branch of a branch

* The above instructions assume we want to create a branch from ```main```. We can also create branches wth use other, different branches as a base...

## Merging up to the head

* In order to keep up to date with changes being made by collaborators to the main branch, we can use git merge main.