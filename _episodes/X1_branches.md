---
layout: page
title: "Creating and using branches for development"
order: 11
session: 2
length: 15
toc: true
adapted: false
---

## Lesson objectives

Understand how to create branches within a GitHub repository
Re contextualise our understanding from session 1 with knowledge of branches
Be able to switch between branches

## Why work on branches

When you are working on an enhancement to an existing piece of software, it's rare that the work can be carried out without complications! It's often that case that your new code will break or clash with an existing aspect of your software, meaning that you need a safe, contained environment to test and debug your changes to the code base before they can be fully introduced.

** Github always works with branches - the first branch is named main and is made the default branch, but technically it is no different from any other kind of branch.
** All of the content from session 1 applies equally to working on a branch as it does to working on "main"


## Creating a branch

First things first, we need to create a new branch. Let's list the current branch we are working on using the command:
```
$   git branch --show-current
```
This should return the name of the default branch, ```main```.
To create and switch to a new branch we use the following command:
```
$   git checkout -b new_branch
```
If we now check which branch we are currently working on, we can see that we have successfully created and switched to the new branch: 

```
$    git branch --show-current
new_branch
```

Lets create a new text file containing some new information. In order to add the new file we need to use ```git add``` (this was covered in episode 7) to stage the changes. Once the file has been staged, we can commit the file to the new branch.