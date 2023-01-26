---
layout: info_page
title: Installation Guide
---

In order to fully participate in this course, you should make sure you
have the following in place **before** the first workshop.

- An [installation of Git](#installing-git) on your computer.
- A [GitHub account](#get-a-github-account).
- A [text editor or integrated development environment (IDE)](#text-editors--ides)
  to use for working with source code / text files.
  <a href="https://code.visualstudio.com/" target="_blank" rel="external noreferrer">Visual Studio Code</a>
  is recommended as it will be used during the workshop sessions, but you
  can use another program if you prefer; [see the discussion below](#text-editors--ides) for
  more information.

This page gives more details on these requirements.

_Please note that installing software, such as Git or a text editor, may require
administrative privileges._


## Installing Git

You should first check whether you have Git installed on your computer, according
to your operating system:

- **Windows:** Search for the application _Git Bash_ on your computer. (You can
  open up a new search by pressing the Windows and `S` keys together.) If you
  find _Git Bash_ as an application, then you already have Git installed.

- **MacOS & Linux:** Open a terminal and run the command `git --version`. If
  you get a response that looks something like

  ```output
  git version 2.25.1
  ```

  then you have Git installed (your version number may differ). On the other
  hand, if you get a response that says something like

  ```output
  Command 'git' not found
  ```

  then Git is not installed.

If you don't have Git installed then you will need install it. Instructions and
recommended sources for doing this are provided below, according to operating
systems.


### Windows

Download and install the latest version of *Git for Windows* from
<a href="https://git-scm.com/download/win" target="_blank" rel="external noreferrer">https://git-scm.com/download/win</a>.
Accept the default settings while running the installer, with the following
optional exceptions:

- On the *Select Components* pane, you may wish to select the option to
  *Check daily for Git for Windows updates*. Selecting this will mean Git for
  Windows will tell you when a new update for it is available.
- On the *Choosing the default editor used by Git* pane, you can select
  a different text editor that will be used to write
  'commit messages' in Git. The default text editor, Vim, is difficult to
  use if you're not used to it. Nano is a much simpler text editor that works
  from the command line, so our recommendation would be to switch to that. The
  choice of text editor can be changed later once Git is installed, so you're not
  tied in by your choice here.


### Mac OS

We recommend installing Git through the
*Xcode Command Line Tools*. This is a collection of software, curated by
Apple, that is useful for developing code on MacOS; Git is one of the programs
included. Daniel Kehoe has 
<a href="https://mac.install.guide/commandlinetools/index.html" target="_blank" rel="external noreferrer">a very good guide</a>
on the Xcode Command Line Tools. Daniel's guide recommends installing the
<a href="https://brew.sh/" target="_blank" rel="external noreferrer">Homebrew</a>
package manager at the same time as the Xcode Command Line Tools,
however this is not required for installing Git, so we instead recommend following
<a href="https://mac.install.guide/commandlinetools/4.html" target="_blank" rel="external noreferrer"> the version of his instructions that avoids installing Homebrew</a>.


### Linux

Install Git using your operating system's package manager. See
<a href="https://git-scm.com/download/linux" target="_blank" rel="external noreferrer">https://git-scm.com/download/linux</a>
for instructions.


## Get a GitHub account

To set up an account, go to
<a href="https://github.com/" target="_blank" rel="external noreferrer">https://github.com/</a>
and click on *Sign Up* in the top right-hand corner. Make sure you know your
username and password for the start of the course!


## Text editors / IDEs

You should also have a text editor or integrated development environment (IDE)
installed on your computer, to give you a means of editing text files and source
code. Throughout this course we will be using
<a href="https://code.visualstudio.com/" target="_blank" rel="external noreferrer">Visual Studio Code</a>
(a.k.a. VS Code) because it has nice integration with Git (it's also free and
works on most operating systems). One or two parts of the course will use
features in VS Code to better visualise what is going on with Git (such as
visualising differences between file versions), so you will likely find it
simplest to use VS Code to follow along in this course.

However, if you don't want to use VS Code then you can use whatever text editor / IDE
you feel comfortable with. Examples include:

- Notepad++
- Sublime Text 
- Emacs
- RStudio (includes Git integration)
- PyCharm (includes Git integration)
- (At the command line) Vim, Nano

You may wish to see if your preferred text editor / IDE has integrations
with Git, or if there are plugins or other extensions that add capabilities for
working with Git from within your text editor / IDE.


### Installing VS Code

Head to <a href="https://code.visualstudio.com/" target="_blank" rel="external noreferrer">https://code.visualstudio.com</a> to download and install VS Code for your operating system.
Windows users can also install it from the Microsoft Store.