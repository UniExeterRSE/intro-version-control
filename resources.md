---
layout: info_page
title: Resources
---

*Please note, this workshop is under development. Links to additional resources or
supplementary material will appear here nearer to the time of the workshops.*


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
<a href="https://swcarpentry.github.io/shell-novice/02-filedir/index.html" target="_blank" rel="external noreferrer">Navigating Files and Directories</a>.


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
> - `/home/jbloggs/respositories/foo/bar/file.txt` is an absolute path to a file
> - `foo/bar/file.txt` is the same file as a relative path
> 
> **List the contents of a directory:** `ls path/to/directory` (or just `ls` to list
> the contents of the current working directory). Use the `-a` option to show
> files that are 'hidden' (i.e. begin with `.`) and use `-l` to give more details
> about the items e.g. to list all contents of home directory with details about
> modification time, access permissions etc:
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