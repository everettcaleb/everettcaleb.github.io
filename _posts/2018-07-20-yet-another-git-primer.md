---
layout: post
title: "Yet Another Git Primer"
date: 2018-07-20
---
This was written for a good friend of mine that was trying to learn Git and how that fits
in with GitHub, pull requests, branching, etc. Hopefully it can serve as a useful primer to
how some people use Git in their day-to-day development. Obviously, I have my own processes and
opinions so my way of doing things may be different than yours.

## So What Is Git? GitHub?
"Git is a free and open source distributed version control system (DVCS) designed to handle everything from small to very large projects with speed and efficiency." ([website](https://www.git-scm.com)) In plain English, it lets developers (or anyone really) synchronize the changes they make to a project, record a history of these changes, and enables flexibility in trying out new ways to code stuff without interfering with the stability of the main project. GitHub fits in here as a provider of a central repository for Git that can be used as the system of record for a project to coordinate between team members. It provides a bunch of other useful features that we'll get into later.

TL;DR: Git lets you track changes to project code. GitHub is a place to store it all, plus extra features.

## How Does It Work?
Git keeps the history of groups of changes (called "commits") and past versions of files along with your current "working copy". A project in Git is stored in a "repository". What makes Git different from other version control systems (VCSs like SVN, TFVC, etc.) is that even your local copy is a complete repository and the full history is recorded on every machine with a copy. This allows development history to be retained and merged together even if multiple developers are working separately/remotely from one another. Another difference is that after making changes that you want to add to the history, you "add" them to a "staging area" so that you can review the group of changes. Once you're sure that's what you want to commit, you commit everything in the staging area and type a message explaining what those changes are for. Some organizations (and open-source projects) have standards or templates that dictate what these commit messages should look like. It's good practice to make the first line of the message a quick summary (almost a TLDR of changes) and then put more details after that. If you're using an issue tracking system (JIRA, GitHub Issues, etc.), you probably also want to put the issue ID in the message (this may even be a rule). Here's what a commit message may look like:

    PROJ-123 Performance tweaks to friends API

    - Removed extra database call to the Friend table that was superfluous
    - Changed math for nearby calculation to use distance squared
    - Moved logging call to after response

The summary is really nice to have so that if team members use Git's one-line history display it shows helpful information.

## Quick Tutorial
Let's jump into a quick walkthrough so you can get familiar with the basic concepts and commands. Git is primarily used from a terminal/command prompt and so I'm going to teach it that way. At the bottom of this page, in references, I'll include links to GUI tools, but it's not super difficult to use from the terminal. On some Linux distros or Mac, you should have Git installed by default. If not, visit the [Git website](https://www.git-scm.com) to install it. On Windows, you definitely need to install it. Just stick with the defaults for the prompts and you should be fine. For a terminal on Windows, I would recommend using Git Bash which is installed with Git for Windows. Some commands may not be available on the regular Windows command prompt, but it's mostly just the Git ones that are important for this tutorial.

First, make a new folder and initialize it as a Git repository:

    mkdir hello-git
    cd hello-git
    git init

Congratulations! You've built a local Git repo. Let's list the contents so you can see what that actually did:

    ls -al

That command should print out something like this (bear in mind I'm on a Mac so yours may look a bit different):

    drwxr-xr-x   3 ceverett  staff   96 Jul 20 12:52 .
    drwx------+  7 ceverett  staff  224 Jul 20 12:48 ..
    drwxr-xr-x  10 ceverett  staff  320 Jul 20 12:52 .git

That `.git` folder is where Git stores the metadata and history for your repository. Unless you're doing something advanced (setting up commit templates, hooks, etc.) you shouldn't need to touch anything in it directly. If this is the first time you've used Git on your machine, you also need to run these commands with your own name and email:

    git config --global user.name "Caleb Everett"
    git config --global user.email "caleb@example.com"

Those commands will set your name and email for commits; both of which will show up in history. Create a text file called "test.txt" in your 
