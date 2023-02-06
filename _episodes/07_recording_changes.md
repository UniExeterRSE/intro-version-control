---
layout: page
title: "Recording Changes"
order: 7
session: 1
length: 15
toc: true
adapted: true
attrib_name: Version Control with Git - Tracking Changes
attrib_link: https://swcarpentry.github.io/git-novice/04-changes/index.html
attrib_copywrite: Software Carpentry
attrib_license: CC-BY 4.0
attrib_license_link: https://creativecommons.org/licenses/by/4.0/
---

## Learning objectives

By the end of this episode you will be be able to record changes made to files
using the `git add` and `git commit` commands. You will understand the difference
between these commands and the general _modify-add-commit_ workflow for building
up a revision history of files in Git.


## Viewing the status of a repository

So, we have a new repository, either a clone from a remote repository or a
brand new, empty one. It's time to get to work adding content to it. But before
we do that, let's cover one of the simplest, yet most useful, Git commands:
`git status`.

The `git status` command gives you information about the current state of a
Git repository. Let's take a look at an example with our recently cloned
`git-good-practice` repository. We first need to make sure that we're located
in the root folder of the repository. In the example below, this is contained
within the parent folder `~/repositories`, so we first change directories with
`cd` and remind ourselves of the contents:

```
$ cd ~/repositories/git-good-practice
$ ls
README.md
```

Currently there's just a single readme file. Recall that the `git-good-practice`
folder actually also contains the hidden folder `.git`, which we would have also
seen if we'd used `ls -a` instead of just plain old `ls`. Now we can check the
status of the repository:

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
Let's consider what the output means:

- The first two lines refer to a *branch* called `main`, and how it's up-to-date
  with another branch called `origin/main`. For now,
  you can regard these lines as saying that our local version of the repository
  is in sync with the remote version. (This is not the whole story and
  is, at best, a partial truth. We'll uncover more about what this really means later
  in the course when we talk about 'pushing'/'pulling' changes to/from the remote
  repository and when we learn about branches.)

- The line `nothing to commit, working tree clean` is of more immediate interest.
  This is Git's way of saying that it hasn't identified any changes to the
  contents of the repository ('working tree clean'), so there are no new changes
  that could be recorded in the repository's history ('nothing to commit').

- Finally, note that `git status` only gives us information about *changes* to
  the contents of the repository. It doesn't spell out the whole contents of
  the repository like `ls` would. For example, we know that the repository
  contains the file `README.md`, yet it doesn't feature in
  the output of `git status` because there aren't any (new) changes to it.

For our purposes, you can think of the **working tree** as the contents of the
repository, just like you're used to thinking of files within a folder or its
subfolders. Git is able to detect changes to files in the repository (including
if files have been added or removed), as well as in subfolders of the repository.


> ### Run `git status` often
> 
> We're going to flag here that you should get into the habit of running
> `git status` often. It's the primary way of seeing at a glance what state
> your repository is in and how the working tree differs (or not) with the state
> of the repository.


## Adding and committing files

Let's make some changes to the repository. First, we'll create a new Markdown
file called `Git-cheatsheet.md`, for us to record key Git commands as we go.
Running `git status` now shows us:

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Git-cheatsheet.md

nothing added to commit but untracked files present (use "git add" to track)
```

The 'Untracked files:' bit indicates that Git has spotted a new file which it
has no record of. Before going further, let's add some content to the cheatsheet
about `git status`:

```
# Git Cheatsheet

*Note: run commands from within a Git repository*


## Checking state of a repo (do this often!)

`git status` — Checks the state of a Git repository.

```

> ### Markdown syntax
>
> * Hash symbols (`#`) are used to denote the document title and headings. One
>   hash `#` denotes the document title, two hashes `##` indicates a section heading,
>   three hashes `###` indicates a sub-heading, etc.
>
> * Wrapping text with asterisks (`*`) will emphasise text i.e. set it in italics.
>   You can also wrap the text in underscores (`_`) e.g. `*This* is in italics,
>   so is _this_.`
>
> * Wrapping text in backticks (`` ` ``) is used to display code. It won't be
>   formatted like regular text. Compare:
>   - Wrapped in backticks: `` `foo _bar_` `` renders as `foo _bar_`
>   - As regular text: `foo _bar_` renders as foo _bar_
>
> * Extra spaces and tabs are just treated as a single space. Paragraphs must
>   have a blank line between them to be rendered on different lines. E.g.
>
>   <table>
>     <tr>
>       <td><strong>Markdown code</strong></td>
>       <td><strong>Rendered output</strong></td>
>     </tr>
>     <tr>
>       <td>
>         <code>No &nbsp; &nbsp; &nbsp; extra spaces here</code>
>       </td>
>       <td>
>         No    extra spaces here
>       </td>
>     </tr>
>     <tr>
>       <td>
>         <code>
>         These lines are in<br>
>         the same paragraph
>         </code>
>       </td>
>       <td>
>         These lines are in
>         the same paragraph
>       </td>
>     </tr>
>     <tr>
>       <td>
>         <code>
>         These lines are in<br>
>         <br>
>         different paragraphs<br>
>         </code>
>       </td>
>       <td>
>         <p>These lines are in</p>
>         <p>different paragraphs</p>
>       </td>
>     </tr>
>   </table>

> ### Previewing in VS Code
> 
> If you're using VS Code as your text editor, you can preview a rendered Markdown
> document by opening the Command Palette (_View_ > _Command Palette..._),
> searching for _Markdown: Open Preview_ and selecting this command. There's also
> and option to open the preview side-by-side with the Markdown source document,
> which is useful when editing.

After adding the above text to `Git-cheatsheet.md` file and saving our changes,
we now tell Git to start tracking changes to this file by using the `add`
command:

```
$ git add Git-cheatsheet.md
```

Let's see what `git status` now tells us:

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   Git-cheatsheet.md
```

The difference between this status and the status before we did `git add` on our
cheatsheet is the 'Changes to be committed:' bit. Git has now recognised that
it has a new file, called `Git-cheatsheet.md`, to keep track of. But it hasn't
yet stored the new version of the file as part of its history. To do that, we
need to run another Git command, called `commit`:

```
$ git commit
```

Upon entering this command, the text editor we configured for Git earlier springs into life, opening up a file with some pre-defined text and leaving space at the top for us
to write in. (The lines preceded by hashes are comments that are ignored by Git.)

```

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch main
# Your branch is up to date with 'origin/main'.
#
# Changes to be committed:
#       new file:   Git-cheatsheet.md
#
```

As you can see, this file is for writing a **commit message**. This is a message
that tells people about changes that are being committed to the repository.
It should briefly, but clearly, describe the main changes that have been made. We
add our commit message at the top of the opened file:

```
Create a cheatsheet document

Start the document by adding an entry for Git's status command.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch main
# Your branch is up to date with 'origin/main'.
#
# Changes to be committed:
#       new file:   Git-cheatsheet.md
#
```

Once we've written our message, we save the document (**don't** change the file
name!) and close it. The `git commit` command finishes and we get a little
summary message about what was just committed (note the first line of our
commit message is included):

```
$ git commit
[main 9e6e24f] Create a cheatsheet document
 1 file changed, 8 insertions(+)
 create mode 100644 Git-cheatsheet.md
```

When we run `git commit`,
Git takes everything we have told it to save by using `git add`
and stores a copy permanently inside the special `.git` directory.
This permanent copy is called a **commit** (or **revision**).

> ### Best practice: commit messages
> 
> <a href="https://chris.beams.io/posts/git-commit/" target="_blank" rel="external noreferrer">Good commit messages</a>
> start with a brief (usually < 50 characters) statement about the
> changes made in the commit. Generally, the message should complete the sentence
> "If applied, this commit will [_commit message here_]".
> If you want to go into more detail, add a blank line between the summary line
> and your additional notes. Use this additional space to explain why you made
> changes and/or what their impact will be. Avoid uninformative messages such as
> "small tweaks" or "updates" — write what will be useful for others to read
> (which includes yourself in one year's time).


If we now run `git status` again, we get the following:

```
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Git is now telling us that:

* There are no further changes in the repository to record
  ('nothing to commit, working tree clean').

* The new version of the repository has been recorded in a commit ("Your branch
  is ahead of 'origin/main' by 1 commit.") The "ahead of
  'origin/main'" bit indicates that our local repository now has new snapshots
  that aren't recorded in the remote repository. We'll discuss this in a later
  episode, so just focus on the "1 commit" bit for now.