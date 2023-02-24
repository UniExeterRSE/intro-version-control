---
layout: page
title: "Merge Conflicts"
order: 17
session: 3
length: 5
toc: true
adapted: false
---

## Learning objectives

In this episode you will be introduced to GitHub issues, a facility for tracking
tasks for code within a GitHub repository. You will also learn how issues can
be used with the feature branching strategy.


## GitHub issues: tracking features

It's been a while since we consulted our TODO list. We can now strike off the
cheatsheet entry for pushing and pulling,
but there are some other tasks we could write down to further improve our
`git-good-practice` repository:

```
TODO:

Add cheatsheet entries for `git rm` and `git mv`

Add cheatsheet entries about undoing changes

Add some material about ignoring files

Add the feature branch merging protocol to Collaboration-good-practice.md

Add some notes about avoiding merge conflicts in Collaboration-good-practice.md

Start a new good practice document with general steps for resolving merge
conflicts
```

Each of these items could be considered a new 'feature' to add to the material
in our repository. In some ways, it would be nice if there was a more integrated
way to keep track of such 'features' in the context of our repository.

Fortunately, GitHub provides the facility to create and manage _issues_ in a
repository. In GitHub, an _issue_ is essentially the same thing as a _feature_,
which we introduced in the episode
[Collaborating with Branches]({{ site.url }}/15_collaborating_with_branches/index.html).
We can create an issue in GitHub for any piece of work that adds to the
software's overall development, whether this be a new piece of functionality, a
bug fix, some documentation, etc. The nice thing about GitHub issues is that
they provide everyone working on the repository with a view of the features
that need implementing. They can also be linked to branches and pull requests,
in such a way that when the PR gets closed, the issue is marked as completed.
Issues are part of some of the more general project management features that
GitHub offers. Have a read about
<a href="https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects" target="_blank" rel="external noreferrer">Projects on GitHub</a>
for more on this.

We encourage you to use issues as part of your software development process when
using GitHub, especially when collaborating with others.


### Issues with feature branching 

Here we will summarise
a typical workflow that you can use with
the feature branching strategy we've discussed in earlier episodes. Links are
provided to the GitHub documentation, where you can read about the mechanics of
performing the stated actions.

When you have a new _feature_ to implement in the code in your repository:

1. <a href="https://docs.github.com/en/issues/tracking-your-work-with-issues/creating-an-issue#creating-an-issue-from-a-repository" target="_blank" rel="external noreferrer">Create a new issue</a>
   to capture what needs to be done. It's good practice to include enough detail
   to enable anyone in your team to pick up the issue and implement it.

2. <a href="https://docs.github.com/en/issues/tracking-your-work-with-issues/creating-a-branch-for-an-issue" target="_blank" rel="external noreferrer">Create a branch for the issue</a>.
   This (remote) branch then becomes the feature branch upon which work is done
   to implement the issue / feature.

3. Once you start work on the issue, create a pull request for the feature
   branch and
   <a href="https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue" target="_blank" rel="external noreferrer">link the PR to it</a>.

4. Once the PR is merged, it should automatically close the issue. If for
   some reason this doesn't occur, of if you need to close the issue for another
   reason (e.g. it no longer needs to be addressed) then you can
   <a href="https://docs.github.com/en/issues/tracking-your-work-with-issues/closing-an-issue" target="_blank" rel="external noreferrer">close it manually</a>.

5. To view all the issues for a repository, go to the repository's main page
   on GitHub and click on the _Issues_ tab. Note that only issues that are still
   open are shown by default, but you can click on the _Closed_ link under
   the _Filters_ search bar to view closed issues if you wish.

You can
<a href="https://docs.github.com/en/issues" target="_blank" rel="external noreferrer">read more about GitHub issues</a>
on GitHub's online documentation. 


### Exercise

Practice the workflow above by completing one of the tasks in the
`TODO.txt` file given at the beginning of this episode. (Even better: do this
for something you've learnt that is _not_ recorded in the TODO
list above.) Create an issue on
GitHub for the task, then implement it using the feature branching strategy, making sure
to link your branch and associated pull request to the issue.
