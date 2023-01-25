---
layout: info_page
title: Installation instructions
---

In order to fully participate in this course, you should make sure you
have the following **before** the first workshop.

- An [installation of Git](#installing-git) on your computer.
- A [GitHub account](#get-a-github-account).
- A [text editor or integrated development environment (IDE)](#have-a-text-editor)
  that you use for working with source code / text files.
  <a href="https://code.visualstudio.com/" target="_blank" rel="external noreferrer">Visual Studio Code</a>
  is recommended as it has nice integration with Git and is free, but you
  can use whatever you're comfortable with; [see below](#have-a-text-editor) for
  more information.

More details on these points are provided below.

_Please note that installing software, such as Git or a text editor, may require
administrative privileges, so you may need to get someone from your
University / organisational IT department to help you. **Be sure to allow enough
time to do this before the start of the course.**_


## Installing Git

You should first check whether you have Git installed on your computer, following
these instructions as per your operating system:

- **Windows:** Search for the application _Git Bash_ on your computer. (You can
  open up a new search by pressing the Windows and `S` keys together.) If you
  find _Git Bash_ as an application, then you already have Git installed.

- **MacOS & Linux:** Open a terminal and run the command `git --version`. If
  you get a response that looks something like
  ```output
  git version 2.25.1
  ```
  then you have
  Git installed (your version may differ). On the other hand, if you get a
  response that says something like
  ```output
  Command 'git' not found
  ```
  then you probably don't have Git installed.

If you don't have Git installed then you will need install it. Instructions and
recommended sources for doing this are provided below, according to operating
systems.


### Windows

Download and install the latest version of *Git for Windows* from
<a href="https://git-scm.com/download/win" target="_blank" rel="external noreferrer">https://git-scm.com/download/win</a>.


### Mac OS

We recommend installing Git through the
*Xcode Command Line Tools*. This is a collection of software, including Git, that
is useful for developing code on MacOS. Daniel Kehoe has 
<a href="https://mac.install.guide/commandlinetools/index.html" target="_blank" rel="external noreferrer">a very good guide</a>
on the Xcode Command Line Tools. Daniel's guide recommends installing the
<a href="https://brew.sh/" target="_blank" rel="external noreferrer">Homebrew</a>
package manager at the same time as the Xcode Command Line Tools,
however this is not required for installing Git, so we instead recommend
following his instructions that avoid installing Homebrew as well,
<a href="https://mac.install.guide/commandlinetools/4.html" target="_blank" rel="external noreferrer">Install Xcode Command Line Tools Directly</a>. 


### Linux

Install Git using your operating system's package manager. See
<a href="https://git-scm.com/download/linux" target="_blank" rel="external noreferrer">https://git-scm.com/download/linux</a>
for instructions.


## Get a GitHub account

Participants should make sure they have a GitHub account before the start of the
course. To set up an account, go to
<a href="https://github.com/" target="_blank" rel="external noreferrer">https://github.com/</a>
and click on *Sign Up* in the top right-hand corner. Make sure you know your
username and password for the start of the course!


## Have a text editor

You should also have a text editor or integrated development environement (IDE)
installed on your computer, to give you a means of editing text files and source
code. Throughout this course we will be using
<a href="https://code.visualstudio.com/" target="_blank" rel="external noreferrer">Visual Studio Code</a>
(a.k.a. VS Code) because it is free, works on most operating systems and has nice integration
with Git. One or two parts of the course will use features in VS Code to better
visualise what is going on with Git (such as visualising differences between
file versions), so you will likely find it simplest to install
VS Code to follow along in this course.

However, if you don't want to use VS Code you can use whatever text editor / IDE
you feel comfortable with. Examples include:

- Notepad++
- Sublime Text 
- Emacs
- RStudio (includes Git integration)
- PyCharm (includes Git integration)
- (At the command line) Vim, Nano

You may wish to see if your preferred text editor / IDE has integrations
with Git, or if there are plugins / extensions that add capabilities for
working with Git from within your text editor / IDE.
