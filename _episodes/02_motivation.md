---
layout: page
title: "Motivation: Why use Version Control Systems?"
order: 2
session: 1
length: 10
toc: true
adapted: false
---

## Learning Objectives

At the end of this episode you will be able to describe what a version control
system is and why they are useful.


## What is a version control system?

A **version control system** is software that enables you to
record and manage the history of versions of files as they change. They are
typically used for tracking the changes to software source code, such as Python
files, R files, C/C++ source files, or other text-based documents like HTML, LaTeX, markdown, etc.
With a version control system, you
make changes to a file (or files) as normal, but then use the version control
system to capture the updated version. You can attach comments to each captured
version to explain the changes made. In this way, you incrementally
build up a history of versions of the file(s). The version control system
allows you to view the evolution of files and 'roll back' to any previous
version you like. It also takes care of storing away this history out of your
day-to-day sight.

So a version control system acts as a record-keeping device. This is useful, but
the real power of a version control system is that that they
_facilitate collaboration_ when multiple
people work on a set of files, such as when a team of people are developing
code. In particular, they provide a set of
tools that allow you to easily share your changes with others and, crucially,
_combine other peoples' changes with your own_. The tooling enables you to do
this in a structured way that makes combining changes transparent
and less error-prone. Furthermore, the histories of each person's changes are
shared with each other, so that the record of changes to files is not split out
amongst multiple person's computers.


## Why bother to use a version control system?

There is, of course, a disadvantage to using a version control system: you need
to learn how to use it. Is it perhaps easier to use other methods to keep track
of versioning your files?

Let's compare version control systems to a couple of other options.

### Cloud-based synchronisation e.g. Google Drive, DropBox, OneDrive/SharePoint

These days there are cloud-based services that allow you to sync your local
files with copies kept in the cloud: e.g. Google Drive, DropBox, OneDrive etc.
These services can keep a record of file versions and allow you to roll back to
previous versions, so why not just use these?

- **Answer 1:** These kinds of features tend to capture versions
  of files as they are saved and are more geared to recovery from e.g.
  accidental deletion or modification. It is almost certain they won't give you an
  organised 'chunking up' of the evolution of a file. For example, perhaps you
  are fixing a bug and end up saving ten times while
  you modify your code and re-run it to see if you've fixed it. It's not very
  helpful to have a history of all these tiny changes: it just makes finding a
  'proper' previous version of the code more difficult. Besides this, the
  log of versions of the file(s) probably won't have any helpful description to
  help you understand the content of each version — you'll likely only get
  a timestamp giving when the file was last modified. With a version control
  system, you control the snapshots of a file's history and provide helpful
  descriptions, so that a more helpful 'story' of the file's evolution is
  recorded.

- **Answer 2**: These services don't offer anything to help with collaboration
  on files. If you want to combine edits to a file from multiple people, you
  need to do things like agree that only one person can work on the file at
  once, which is cumbersome. They also don't give a way for you to quickly view the
  changes that were made to a file by someone else. Version control systems
  address both of these shortcomings.


### Multiple versions of files locally

Have you ever created a folder of code that ends up looking something like
this?

![Versioning software with chaotic file names](../images/folder-chaos.png)

Sure, you can remember which of these files you need to use as you're in the
thick of developing your code. But what about when you come back to it a
month later?

... Or 6 months later?

... Or three years from now, after the paper is _finally_ published and you've
moved onto other things, when all
those little bits of working knowledge of the code have evaporated into the
mists of time (make no mistake, they _will_ evaporate), when an email pops into
your inbox from someone who has 'just a
small query' about the validity of your findings, and asks if you can send them
the code used to generate the results?

Which files would you send?

Wouldn't you rather turn back to that folder and find this?

![A clean folder of software](../images/folder-calm.png)

(Note: the `.git` folder is particular to the version control system Git,
which you'll learn about in this course!)

Even if you're much more disciplined about keeping versions of your files than
the chaotic example above, it's worth considering the following:

* Your system probably doesn't help you much when collaborating with others, like
  when you need to merge changes from others into your code. Version control
  systems include tools to help with this.

* If you work together with others on the same files, do they follow the same
  conventions for keeping track of versions as you? If everyone is using the
  same version control system, then this provides consistency of approach.

* Let's face it, keeping up a discipline of manually versioning your files is a
  drag, and will likely go out the window when the pressure of a deadline starts
  biting. Using a version control system significantly reduces the effort
  required to keep a good, orderly record of development, and to combine your
  work with others'. Sure, it still requires discipline to use a version control system,
  but like all good disciplines it helps to _make your life easier and lighter_.
  In quite a short space of time, using a version control system just becomes
  part of your rhythm of work.


## Note for the course

In this episode we have talked about version control systems being used to
keep track of the evolution of files in general. Going forward, we will
discuss the use of version control in the context of developing code for
software, particularly in a research setting. Software development is the
common context in which version control systems are used.
