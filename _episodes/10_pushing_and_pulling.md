---
layout: page
title: "Pushing to and Pulling From the Remote Repository"
order: 10
session: 1
length: 15
toc: true
adapted: false
---

## Lesson objectives

TODO (summarise main learning points in a few sentences)


## Pushing to the remote

By now we've done quite a bit of work on our cheatsheet and good practice
material in our local `git-good-practice` repository. It seems like a good point to
put this work on the remote repository residing on GitHub.

Let's review the status of the repository and view the log:

```
$ git status
On branch main
Your branch is ahead of 'origin/main' by 11 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

$ git log --oneline
92b2ac2 (HEAD -> main) Create general good practice guides directory
5cf8321 Remove rubbish.txt
d26a698 Add some rubbish to try out 'git rm'
910bb79 Add note about '--name-only' option to 'git diff'
9bb2714 Add entries about 'git diff' to cheatsheet
37be130 Add entry about 'git log' to cheatsheet
46b11e6 Add advice on committing little and often
ecbf67e Add entry for 'git commit' with '-m' option
34c19f2 Add material on committing
ad56194 Add entry about staging files with 'git add'
17912ce Create a cheatsheet document
3917168 (origin/main, origin/HEAD) Initial commit
```

The status indicates `main`, our local *branch*, is ahead of `origin/main`, the
remote *branch*, by 11 commits. These commits are our new snapshots that are yet
to be recorded in the remote repository. The log shows the short identifier and
commit message of each of these commits, along with the initial commit generated
when the repository was created (`3917168`).

The status also includes a handy comment, suggesting "use "git push" to publish
your local commits" - this is exactly what we should do next! Ultimately, `git push`
transfers the commits we've made in our local repository to the remote repository.
It should be noted that it will only push _commits_, not changes residing in the
working tree or staging area. We can alternatively use `git push origin`, if we'd
like to be more explicit about which remote repository we are pushing to (`origin`
by default).

TODO:
* Explain that we may be prompted to enter our Git username and a password.
  Because we set up the repository to work with HTTPS, we use the Personal
  Access Token (PAT) that we generated in the episode
  [Setting up Git and GitHub]({{ site.url }}/04_configuring_git/index.html)
  - Add a tip that you can paste the PAT in most terminals by right-clicking
    at the prompt

We now push the commits to our remote `git-good-practice` repository (note
that our terminal program doesn't display the PAT when we paste it in):

```
$ git push origin
Username for 'https://github.com': jbloggs9999
Password for 'https://jbloggs9999@github.com':
Enumerating objects: 33, done.
Counting objects: 100% (33/33), done.
Delta compression using up to 8 threads
Compressing objects: 100% (31/31), done.
Writing objects: 100% (32/32), 4.09 KiB | 1.02 MiB/s, done.
Total 32 (delta 13), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (13/13), done.
To https://github.com/jbloggs9999/git-good-practice.git
   3917168..92b2ac2  main -> main
```

Now we check the status and log again:

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

$ git log --oneline
92b2ac2 (HEAD -> main, origin/main, origin/HEAD) Create general good practice guides directory
5cf8321 Remove rubbish.txt
d26a698 Add some rubbish to try out 'git rm'
910bb79 Add note about '--name-only' option to 'git diff'
9bb2714 Add entries about 'git diff' to cheatsheet
37be130 Add entry about 'git log' to cheatsheet
46b11e6 Add advice on committing little and often
ecbf67e Add entry for 'git commit' with '-m' option
34c19f2 Add material on committing
ad56194 Add entry about staging files with 'git add'
17912ce Create a cheatsheet document
3917168 Initial commit
```

TODO:
* Point out that we have no outstanding commits to push and that `main` and
  `origin/main` are now located at the same commit. Explain that this means
  the remote repository is up to date with the local repository.


## Viewing the repository on GitHub

TODO:
* Create written instructions for viewing the commits in the remote repository.
  Assume that the repository is under a user's personal account.


## Pulling changes from a remote repository

TODO:
* Explain how platforms like GitHub can be used to share our code with the world.
* Explain what `git pull` does, in the context of an example where we're using
  code from somebody else's repository and want to update our local version with
  the latest release. Perhaps use a 'proper' code repository as the example e.g. for
  some Python package (tensorflow? numpy?...)

TODO:
  * Explain that what we've covered in this episode is suitable in cases where
    we're working alone on our repository. If we are collaborating, we need to
    be more careful in how we use `git push` and `git pull` to avoid conflicts
    with other peoples' work. This will be explored much more in later
    episodes.

