---
layout: info_page
title: Resources
---

## Resources for learning Git

There is a wealth of information online about using Git and many tutorials
have been written before. Below are a selection of resources you may find
helpful as you learn to use Git.

* The Software Carpentry's
  <a href="https://swcarpentry.github.io/git-novice/" target="_blank" rel="external noreferrer">Version Control with Git</a>
  course, on which this course it based.

* Atlassian's <a href="https://www.atlassian.com/git/tutorials" target="_blank" rel="external noreferrer">Git tutorial</a>
  is readable and comprehensive.

* The <a href="https://www.atlassian.com/git/tutorials" target="_blank" rel="external noreferrer">Pro Git</a>
  book. More advanced, but an excellent reference.

You can, of course, also refer to the manual pages to Git or Git commands, by
running `man git` or `git <command> --help` (e.g. `git commit --help`) at the
command line. These are an excellent reference, but they are technical in nature
and can be challenging to newcomers. The second form is useful to see what optional
arguments are available for commands.


## GitHub help

The best place to learn about how to use GitHub is to go to the documentation
section of their website: <https://docs.github.com/en>.


## Command line navigation

Although not strictly required, participants will find it helpful to have a
basic familiarity of working at the command line on a Unix system (MacOS or
Linux). We include Windows users here, since the workshop will work with the
Git Bash program on Windows, which emulates a Unix Bash shell.

All that is required to follow the course is knowledge of how to navigate
around the file system within a Unix-like shell and list the contents of
directories. For convenience, we have included a cheat sheet of Unix command
line navigation below. Throughout the course, we'll only briefly remind
participants of requisite commands, so if you aren't familiar with these aspects
then we encourage you to learn about this ahead of time.
You can do this at the Software Carpentry's course on the Unix shell, which has
a section on
<a href="https://swcarpentry.github.io/shell-novice/02-filedir/index.html" target="_blank" rel="external noreferrer">navigating files and directories</a>.


> ### Unix command line navigation cheat sheet
> 
> *Note: the shell prompt is denoted `$` in the following examples.*
> 
> **Syntax:**
> 
> - Directories and files in a path are separated by `/`.
> - `~` means your home directory (type `echo ~` to see what this is on your computer).
> - `.` refers to the current directory, `..` refers to the parent directory. Note
>   the latter can be chained e.g. from within the directory `/home/jbloggs/foo/bar/baz/qux`, the directory `../../..` corresponds to `/home/jbloggs/foo`.
> 
> **Print the current working directory** with the `pwd` command e.g.
> 
> ```
> $ pwd
> /home/jbloggs/repositories
> ```
> 
> **File paths can be _absolute_ or _relative_** e.g. from the current
> working directory `/home/jbloggs/repositories` above:
> 
> - `/home/jbloggs/repositories/foo/bar/file.txt` is an absolute path to a file
> - `foo/bar/file.txt` is the same file as a relative path
> 
> **List the contents of a directory:** `ls path/to/directory` (or just `ls` to list
> the contents of the current working directory).
> - Use the `-a` option to show files and directories that are 'hidden' (i.e.
>   begin with `.`).
> - Use `-l` to give more details about the items (permissions, modification time, etc).
> 
> For example, first list (non-hidden) items in the home directory, then list all 
> contents with details:
> 
> ```
> $ ls ~
> repositories
> $ ls -al ~
> total 36
> drwxr-xr-x 5 jbloggs jbloggs 4096 Jan  5 09:41 .
> drwxr-xr-x 5 root       root       4096 Dec 14 09:48 ..
> -rw------- 1 jbloggs jbloggs  745 Jan 19 10:47 .bash_history
> -rw-r--r-- 1 jbloggs jbloggs  220 Dec 14 09:48 .bash_logout
> -rw-r--r-- 1 jbloggs jbloggs 3772 Jan  5 09:40 .bashrc
> drwxr-xr-x 2 jbloggs jbloggs 4096 Dec 14 09:55 .landscape
> drwxrwxr-x 3 jbloggs jbloggs 4096 Jan  5 09:40 .local
> -rw-rw-r-- 1 jbloggs jbloggs    0 Jan 26 10:25 .motd_shown
> -rw-r--r-- 1 jbloggs jbloggs  807 Dec 14 09:48 .profile
> drwxrwxr-x 4 jbloggs jbloggs 4096 Jan 19 09:43 repositories
> ```
> 
> **Change into a directory:** `cd path/to/directory` e.g.
> 
> ```
> $ pwd
> /home/jbloggs/repositories
> $ cd /home/jbloggs/repositories/foo/bar
> $ pwd
> /home/jbloggs/repositories/foo/bar
> $ cd ../../baz
> $ pwd
> /home/jbloggs/repositories/baz
> ```
>
> #### Licence
>
> <p class="copyright">
> This cheat sheet is © 2023 University of Exeter. The material in it other than code snippets and example
> programs is licensed under <a href ="https://creativecommons.org/licenses/by/4.0/">Creative Commons BY 4.0</a>. It has been adapted from
> <a href="https://swcarpentry.github.io/shell-novice/02-filedir/index.html" target="_blank" rel="external noreferrer">The Unix Shell - Navigating Files and Directories</a>
> which is © Software Carpentry and licensed under <a href ="https://creativecommons.org/licenses/by/4.0/" target="_blank" rel="external noreferrer">CC-BY 4.0</a>.
> The code snippets and example programs on this page are MIT licensed, according
> to the 'Software' section of the <a href="{{ site.url }}/LICENCE">licence notice</a>
> for this website's code repository.
> </p>
