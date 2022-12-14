<!--Intro-->
# Introduction
![Git/GitHub](pics/2.png)
## What is Git?
Git is a popular version control system. It was created by Linus Torvalds in 2005, and has been maintained by Junio Hamano since then.

It is used for:

* Tracking code changes
* Tracking who made changes
* Coding collaboration
## What is usually done using Git
* Initialize Git on a folder, making it a Repository
* Git now creates a hidden folder to keep track of changes in that folder
* When a file is changed, added or deleted, it is considered modified
* You select the modified files you want to Stage
* The Staged files are Committed, which prompts Git to store a permanent snapshot of the files
* Git allows you to see the full history of every commit.
* You can revert back to any previous commit.
* Git does not store a separate copy of every file in every commit, but keeps track of changes made in each commit!
## Why Git?
![Example](pics/1.png)
* Over 70% of developers use Git!
* Developers can work together from anywhere in the world.
* Developers can see the full history of the project.
* Developers can revert to earlier versions of a project.

---
## [How Git actually works !](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects "Git Objects Documentation")

---
## GitHub
* the largest host of source code in the world, and has been owned by Microsoft since 2018.
* It's not the same as Git but it uses Git.
---
---
# Installation
## Git
### Linux
```Bash
sudo apt update
sudo apt install git
```
### Windows
[Download Git](https://git-scm.com/)

## GitHub Desktop
[Linux](https://gist.github.com/berkorbay/6feda478a00b0432d13f1fc0a50467f1)

[Windows](https://desktop.github.com/)

### Check installation from Git version
```Bash
git --version
```
![Terminal](pics/4.png)

## Configure Git
> Use **global** to set the username and e-mail for every repository on your computer.

```Bash
git config --global user.name "Muhammad Sabry"
git config --global user.email "test@gmail.com"
```

## Creating Git Folder
```Bash
mkdir GP
cd GP
git init
```
## Git status
To check for any changes in the tracked directory.

```Bash
git status
```
![Terminal Example](pics/5.png)

---
---

## Git Staging Environment
* adding single file.
```Bash
git add script.py
```
* Adding more than one file using regex.

```Bash
git add *.png
```
> The previous command will add all unstaged pictures with png extension in the current directory.

* Adding all changes.

```Bash
git add --all
git add -A
git add .
```
Using **--all** instead of individual filenames will **stage** all changes (new, modified, and deleted) files.

---
---

## Git Stash

Temporarily shelves changes you've made to your working copy so you can work on something else, and then come back and re-apply them later.

![stash](pics/hero.svg)

* Stashing Unstaged changes.

```Bash
git stash -u
```
![terminal example](pics/Screenshot%20from%202022-11-08%2023-33-18.png)

* Stashing Staged changes.

```Bash
git stash
```
![terminal example](pics/Screenshot%20from%202022-11-08%2023-27-42.png)

* Bringing back Stashed work.

```Bash
git stash pop
```
Popping your stash removes the changes from your stash and reapplies them to your working copy.

* Alternatively, you can reapply the changes to your working copy and keep them in your stash.

```Bash
git stash apply
```
* Manging multiple Stashes.

```Bash
git stash list
```

* Adding a message to the stash.

```Bash
git stash save "A brief message"
```

* Popping a specific Stash form Stash list.

```Bash
git stash pop stash@{index}
```

![terminal example](pics/Screenshot%20from%202022-11-08%2023-58-32.png)

* Dropping a specific Stash.

```Bash
git stash drop stash@{index}
```

![terminal example](pics/Screenshot%20from%202022-11-09%2000-00-05.png)

* To clear your Stash.

```Bash
git stash clear
```

![terminal example](pics/Screenshot%20from%202022-11-08%2023-29-13.png)

---
---

## Git Commit

Since we have finished our work, we are ready to move from **stage** to **commit** for our repo.

* Adding commits keep track of our progress and changes as we work. Git considers each commit change point or "save point".
* When we commit, we must include a message **(Mandatory)**.

```Bash
git commit -m "A brief Message"
```

The **commit** command performs a commit, and the **-m "message"** adds a message.

![Terminal Example](pics/Commit-m.png)

* Adding **Description** with the Commit Message.

```Bash
git commit -m "A brief Message" -m "Description ........"
```

## Git Commit with Stage

```Bash
git status
git commit -am "A brief message"
```

>The **-am** allows us to add and message at the same time.

**Note**: to use -am you must check the status first and it's working with already added files not new created ones.

## Git Commit without Stage

Check the status of our repository. But this time, we will use the --short option to see the changes in a more compact way:

```Bash
git status --short
```
> * ?? - Untracked files
> * A - Files added to stage
> * M - Modified files
> * D - Deleted files

**Skipping Staging Environment is not generally recommended.**

## Git Commit Log

Allows us to view the history of commits for a repository.
```Bash
git log
```

![Terminal Example](pics/6.png)

To avoid the very long log list, it's better to use **--oneline** displaying every commit with it's **hash** and **message**.
```Bash
git log --oneline
```
![Terminal Example](pics/oneline.png)

---
---
## Git diff

>It simply displays the changes between two commits

```Bash
git diff #commit1hash #commit2hash
```
>Note: change the order of the commits affects the result as it displays the changes from **commit1** and **commit2**.

![Terminal Example](pics/diff.png)

---
---


## Git Branch

A **Branch** is a new/separate version of the main repository.

Using **Branches** allows you:

* Working on a new version without impacting the live version
* Creating a new branch to fix small errors then merge it to the live version.
* divide the work between more than one person working on independent units.
* You can switch between different **Branches** and work on them without impacting eachother.

### Craeting New Branch

```Bash
git branch NewBranchName
```

### To check on Created Branches

```Bash
git branch
    NewBranch
  * master
```
the **\*** refers to that we are currently on that **Branch**.

To navigate between **Branches** 
```Bash
git checkout NewBranch  #Old Command
git switch NewBranch
```

![Terminal Example](pics/checkout.png)

That command switches us to **NewBranch**.

```Bash
git checkout -b MyNewBranch
```
Using **-b** on **checkout** will create a new **branch** if it doesn't exit then it will navigate to the new created **branch**.

## Merge Branches

First we need to navigate to our destination branch which will have the merged version and it's usually the **master branch** .

Then we **merge** the master branch with NewBranch.

```Bash
git checkout master
git merge NewBranch
```

Since we finished the work on **NewBranch** we can delete it.

```Bash
git branch -d Newbranch
```

![Terminal Example](pics/deletingBranch.png)

## Merge Conflicts

>Merge Conflict happens when there's two versions of the same file in the master and the other branch due to **commits on the destination branch** to fix the conflict we edit the file with the conflict **in the destination branch** then we run **git commit** that will conclude the **merge**.

---
---

## Git Revert

This Command is used when we want to take a previous commit as a new commit.

1. Find that previous commit.

1. Calculate the number of steps.

1. Make it the new commit.

![rev1](pics/img_revert_part1.gif)

```Bash
git log --oneline
```
If it's the previous commit

```Bash
git revert  HEAD --no-edit
```
Adding **--no-edit** to replace the commit message with default revert message.

To **revert** to an earlier commit, use **HEAD~x** where **x** refers (**Number of steps -1**).

```Bash
git revert HAED~2 --no-edit
```
It will make the 3rd previous commit the new one.

![rev2](pics/img_revert_part2.gif)

---
---
## Git Reset
**reset** is the command we use to move the repository to an earlier commit without making new commits.

1. Find that previous commit.
1. Get that **commithash**
1. Move the repository back to it.

```Bash
git log --oneline
```
Get the hash, then

```Bash
git reset 9a9add8
```

## Git Undo Reset

>Even if the following commits are no longer displayed in the log but they still exist.

>Store the **commithash** before applying the reset so you can get back to any commit.

```Bash
git reset e56ba1f
```
>So **reset** could be used to go backward or forward.

---
---
## Git Amend

It combines the latest staging changes with the latest commit as a **new commit** replacing the old one.

>Usually used to change the latest commit message.

```Bash
git commit --amend -m "New message"
```
---
---
## Git ignore

>.gitignore file allows us to ignore the changes of specific files as it uses regex to ignore this group of files and folders.

1. After intializing the repository, create **.gitignore** file.

1. Adding the regex of wanted untracked files.

> Note: Search in google for the .gitignore file for the programming language that will be used in that project, copy it then paste in the created **.gitignore** file.

```Bash
nano .gitignore
```
![ignore rules](pics/ignorerules.jpg)

---
---
## Finally a Cheat Sheet with Extra Information

![Cheat Sheet](pics/cheatSheet.png)

---
---
## Git Help

To see all possible commands.

```Bash
git help --all
```

Or through

[Git Online man Page](https://git-scm.com/docs/git "Git Documentation")

---
---
## Resources

### [**w3schools**](https://www.w3schools.com/git/)

### [**Programming with Mosh**](https://www.youtube.com/watch?v=8JJ101D3knE)

### [**Missing Semester**](https://www.youtube.com/watch?v=2sjqTHE0zok&t=40s)

### [**Bitbucket**](https://www.atlassian.com/git/tutorials/what-is-version-control)