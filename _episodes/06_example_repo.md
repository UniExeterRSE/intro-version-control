---
layout: page
title: "An Example Repository"
order: 6
session: 1
length: 5
toc: true
adapted: false
---

## An example repository

To help you get familar with working with Git and GitHub, we encourage you to
work through an example repository, which you will populate through exercises
that appear in episodes throughout this course. We'll use the repository to
begin building up a cheat sheet of Git commands, some tips on good practice and
links to further resources.


### Markdown

We'll be writing the material for this example repository using
[Markdown](https://en.wikipedia.org/wiki/Markdown). Markdown is a simple markup
language that is well suited to writing documentation for software, or
communicating about code. Many applications, such as the
[VS Code text editor](https://code.visualstudio.com/docs/languages/markdown#_markdown-preview),
can understand and render Markdown files in a visually appealing way.
You write Markdown in files with a `.md` and the syntax is such that even
if you just view a Markdown file as a text file, it looks neat and tidy.
Beyond this, GitHub has support for understanding Markdown throughout its
website and automatically renders Markdown files. As a case in point, the
README file it can generate when you create a new repository is a Markdown
file. It doesn't take long to get up to speed with Markdown and we feel it's
worth the effort to learn.

One slight complication is that there are different _flavours_ of Markdown i.e.
variations on the syntax. The [basic syntax](https://www.markdownguide.org/basic-syntax/) is pretty much uniform across different
flavours, but different flavours provide different ways to extend the basic
syntax to handle more complicated features (such as tables). We'll use the
GitHub Flavoured Markdown, since (surprise!) this is what is used on GitHub. You
can find a pretty comprehensive introduction to the syntax of GitHub Flavoured
Markdown at
<https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax>.

> #### Note
>
> If you're using VS Code to view Markdown docments, note that not all aspects
> of GitHub Flavoured Markdown are supported. For example, task lists are not
> rendered in the VS Code Markdown viewer.

It isn't necessary to know Markdown to follow the examples in this course — we'll
point out bits of Markdown syntax as we go.


## Creating the repository

Our first exercise is to create this repository on GitHub and clone a local
version.

> ### Exercise
>
> Using the instructions in the [_Making Repositories_ episode](./05_making_repos.md):
>
> 1. Create a new repository on GitHub called `git-good-practice`.
>    When doing this, have GitHub generate a readme file for you as part of the
>    repository creation, but otherwise accept the default options. We suggest
>    creating this as a _private_ repository in your personal GitHub account.
>
> 2. Clone the repository just created on GitHub to your own computer, making
>    sure the repository is cloned into a folder called `git-good-practice`
>    (note that this is the default behaviour of `git clone`.)