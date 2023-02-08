---
layout: page
title: "Recording Changes Revisited"
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

By the end of this episode, you will understand how to incrementally stage changes
in a file. You will also learn how to more flexibly refer to files in Git commands
with pathspecs. Finally, you will be able to delete and move files that are
under version control within a Git repository.


## Staging in steps

The last exercise in the previous episode,
[Viewing History and Changes]({{ site.url }}/08_history_and_changes.md/index.html),
began to touch on an important point about staging changes to files. It is possible
to stage some changes to a file, then make further changes to the _same_ file.

For example, suppose we want to start adding content to `Git-cheatsheet.md`
about `git diff`:

```

## Viewing changes

`git diff <files>` — Show changes to files that have not yet been staged.

`git diff <commit1> <commit2> <files>` — Show the differences in files between
                                         two commits.

```

Let's stage these changes:

```
$ git add Git-cheatsheet.md
```

Now let's add some content about the `--name-only` optional argument for
`git diff` to the cheatsheet:

```
`git diff --name-only ...` — Only show the names of files that have changed.

```

Now run `git status`:

```
$ git status
On branch main
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   Git-cheatsheet.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Git-cheatsheet.md

```

`Git-cheatsheet.md` appears as a file that has both changes to be staged and
also further changes that have not yet been staged, which makes sense. From
here, we could

* commit the staged changes (i.e. the content about `git diff <files>`
  and `git diff <commit1> <commit2> <files>`),
  leaving the material about `git diff --name-only ...` as 'work in
  progress' in the working tree; or

* stage the further changes about `git diff --name-only ...`, so that
  they join what's already been staged; or

* leave things as they are and continue working on files in the repository.

This gives us a lot of flexibility to make our commits nice and tidy. Let's go
for the first option. We make the commit and then view the remaining changes
left in the working tree:

```
$ git commit -m "Add entries about 'git diff' to cheatsheet"
[main 9bb2714] Add entries about 'git diff' to cheatsheet
 1 file changed, 8 insertions(+)

$ git diff
diff --git a/Git-cheatsheet.md b/Git-cheatsheet.md
index 75e4430..acff2ee 100644
--- a/Git-cheatsheet.md
+++ b/Git-cheatsheet.md
@@ -34,3 +34,5 @@

 `git diff <commit1> <commit2> <files>` — Show the differences in files between
                                          two commits.
+
+`git diff --name-only ...` — Only show the names of files that have changed.

```

As expected, the changes left to stage are about the `--name-only` option. Let's
tidy up by doing a round of 'add-commit' on these changes, then viewing the log
to see our last two commits:

```
$ git add Git-cheatsheet.md

$ git commit -m "Add note about '--name-only' option to 'git diff'"
[main 910bb79] Add note about '--name-only' option to 'git diff'
 1 file changed, 2 insertions(+)

$ git log -2 --oneline
910bb79 (HEAD -> main) Add note about '--name-only' option to 'git diff'
9bb2714 Add entries about 'git diff' to cheatsheet
```


## Pathspecs

So far, we have been specifying files individually whenever we want to act on
them with Git. Git has its own mini-language for referring to files, which
provides convenient shorthands for referring to multiple files at once. This is
done through what are called **pathspecs**. We aren't going to cover everything
there is to know about pathspecs, but here are some examples:

* `.` refers to files in the current working directory and all directories
  descended from it (e.g. would include `./foo/bar/baz/file.txt`)

* Specifying a directory `foo` will limit to files that descend from `foo`
  (e.g. `./foo/bar/baz/file.txt` but not `./qux/bar/file.txt`)

* `*.py` refers to all `.py` files in the current working directory.

* `foo/*.py` matches all `.py` files in the directory `foo`

Amongst other thing, this can be useful for selecting files to stage. For example,
if our current working directory was the root folder of a Git repository, the
following would add all files anywhere in the root folder or descended from it:

```
$ git add .
```

Alternatively, if we only wanted to stage files descended from the directory
`foo`:

```
$ git add foo/
```


## Deleting and moving files

Sometimes we may need to delete, move or rename files that are under version control
in a repository. Git has specific commands to do this: `git rm` for deletion
and `git mv` for moving and renaming. The key things to remember about these
commands is:

* they only work when applied to files under version control (i.e. that feature
  in commits in the repository); and

* they perform the deletion / move _and then stage the result_, ready for committing.


> ### Comparison with `rm` and `mv`
> 
> You may be familiar with the Unix commands `rm` (for deleting files) and
> `mv` (for moving files). If you use these commands on files that are under version control,
> then the changes will be detected by Git but not staged. The `git rm` and `git mv`
> versions automatically perform the staging for you. If a file is not under
> version control, then you should use the usual Unix commands for deletion and
> moving.


### Deletion

The general form for deleting files that is under version control is

```
git rm <files>
```

Let's create a new file, `rubbish.txt` that we'll put in the root folder
of the `git-good-practice` repository. For the purposes of demonstration, we'll
commit this file and then delete it. First, we create a commit for the file:

```
$ git add rubbish.txt

$ git commit -m "Add some rubbish to try out 'git rm'"
[main d26a698] Add some rubbish to try out 'git rm'
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 rubbish.txt
```

Now we apply `git rm` on the `rubbish.txt` file and check the status after having
done so:

```
$ git rm rubbish.txt
rm 'rubbish.txt'

$ git status
On branch main
Your branch is ahead of 'origin/main' by 9 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    rubbish.txt
```

The deletion has been staged, but not yet committed to the repository. Moreover,
if we view the contents of the folder with `ls`, we can see the file has been
deleted from the file system:

```
$ ls
Commit-good-practice.md  Git-cheatsheet.md  README.md
```

We then commit the deletion to the repository in the usual way:

```
$ git commit -m "Remove rubbish.txt"
[main 5cf8321] Remove rubbish.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 rubbish.txt
```


### Moving

The general form of the `git mv` command is:

```
git mv <source-file> <destination>
```
Note that if `<destination>` is a directory, the file will be
moved there but keep the same name; otherwise, the file will be renamed to
`<destination>`. Note that the directories in the destination path must already
exist. Here are some examples:

* If `foo/bar` is an existing directory path from the current working directory,
  then `git mv file.txt foo/bar/baz.txt`
  will move the file `file.txt` to the new file `./foo/bar/baz.txt` (and stage this
  move).

* If `foo` is a directory, then `git mv file.txt foo` will move `file.txt` to
  `./foo/file.txt`

* `git mv file.txt newfile.txt` will rename `file.txt` to `newfile.txt`.


### Exercise

We will want to create more 'good practice' files as we go through this course,
so let's prepare by moving `Commit-good-practice.md` to a directory called
`Good-practice-guides` in the root folder of the repository. Make this directory
and then create a commit that moves `Commit-good-practice.md` to this
directory.