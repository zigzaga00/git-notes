# Git and Github

## Introducing Git

### What is Git?

Git is a *version control system* (vcs) which is used worldwide and the most popular vcs in use.

Version control software lets us track changes to software over time. We can revisit earlier versions of files, look at changes made and even undo changes. There is lots of version control software around though git is the most popular.

### What Does Git Give Us?

Git helps us to:

- Track changes across multiple files
- Compare versions of a project
- Go back to previous versions
- Revert to previous versions
- Collaborate and share our changes
- Combine our changes with those of others

It is an excellent way to facilitate collaboration on projects.

One example of how git helps us is to think about computer games. We like to save our progress so we do not have to go right back to the start. Git lets us make checkpoints in a similar way because we can go back to a previous point if we mess something up.

Another example is when we are writing a report and keep saving new versions of it - git helps us avoid needing to do this as we can create *checkpoints*.

We can create *checkpoints* after we have developed something in our project.

We can also branch off from checkpoints to develop projects in different ways.

We can combine our work with other developments.

### Git and Github

Git runs on local machines to enable version control. It does not require network access.

Github is an online service which hosts git repositories (projects) so people can work collaboratively online. Github is essentially an online place to share work that is done using git.

## Git Installation and Setup

We can use *graphical user interfaces* (guis) with git but it is much more common to use a *command line interface* (cli).

We can use the *apt* package manager to install git. First, we need to update our repositories using `sudo apt-get update` We can then install git using `sudo apt install git` We can check it installed okay by checking the version with `git --version`

### Configuring Git Name and email

We do not need an account with a password in order to use git but we do need to specify a name and email. This is so we can see who has worked on a project.

To set the git name we can use `git config --global user.name "zigzaga00"`

We can then use `git config --global user.email "zz00@zz00.com"` to set the email used by git.

If we are using github it makes sense to link these creds with those we use on that site.

## Core Git Commands

### Git Repositories

Git repositories (repos) are workspaces which track changes to files inside directories. Anytime we want to use git, we need to create a new repo. Each repo will have their own histories.

We create git repos inside the directories we are working on our projects in.

We can have lots of different git repos on our local machine.

### Git Init and Git Status Commands

We can *instantiate* a new repo using `git repo`

We can check the status of a repo using `git status` inside the repo.

When we want to work with git, we need to first of all *initialise* a git repo - we will do this in the top level directory of our project. Once we are in that directory we just need to run `git init`

#### .git directory

When we *initialise* a git repo, a hidden directory called *.git* is created inside the directory we run the command `git init` This is where git and its related data is kept. We do not want to delete this directory since it contains all the history of the git repo.

#### Common Problem

Git tracks all child directories inside the top level directory in which the initial repo is initialised.

A common problem is when people initialise a git repo *inside* another git repo. In order to avoid this problem we can use `git status` before running `git init` to make sure that we are not somewhere inside an existing repo.

### Git Commit Workflow

The git commit is the most important feature in git.

A git commit is how we make checkpoints in our git projects. We do this after we have altered the project in some way.

The basic workflow here is to amend a project and then commit the changes. We can then make further changes and commit them.

We like to add messages each time we make a commit to a project. This message is best related to the changes which have been made.

A git commit is not just saving a file. A git commit works with git - we can have lots of different changes in one commit which means we will have saved lots of different files before we commit the changes which we have made to them.

We can group changes we have made and place them into one commit which has a relevant message.

This means that there are two commands for us to use when we are commiting work to git. The first is `git add` which lets us select the changes we want to include in the commit. There is then `git commit` which commits those changes.

#### Git Add

We use the `git add` command to stage (select) the changes we want to commit. We add the changes we want to commit to the repo into a staging area by using the `git add` command.

We can use `git add` to stage new files or files we have worked on. We can use a blank space to seperate the files if we are staging more than one.

If we want to stage all changes made, we can use `git add .`

#### Git Commit

We use the `git commit` command to commit the staged files to the repo.

We include a *commit message* when we make a commit - the message needs to summarise what we have done.

When we use `git commit` our default text editor will be opened so we can add the *commit message*. We can use `git commit -m "commit message goes here"` to save time or avoid having a text editor open.

We can stage all changes made in a repo and then commit them using `git commit -a -m "message here"`

##### Tense of Commit Messages

We will see commit messages in both the present and past tense. The imperative form of verbs tends to be used with the present tense. Both ways are okay - the main thing to remember is to keep it consistent across a project. If we are working with others we will need to use the style which they are using.

#### Changing the Default Message Editor

We can change the default message editor with `git config --global core.editor "code --wait"`

In this example, we are setting *vscode* to be the core editor - we will need to add the *code* command to the path - we can do this using the *command palette* in *vscode*.

### Git Log

The `git log` command shows us a log of the commits which have been made to a repo.

The data returned by this command includes data about who made the commit along with when they made it, their contact details and commit message. There is a *commit hash* at the top of each entry.

We can format the log data so we do not have to see long commit messages using `git log --oneline` which is the *shorthand* for `pretty=oneline`

### Atomic Commits

Keeping git commits *atomic* refers to how we should try to keep our commits to be based around a single idea - this might be the development of a feature or the addition of a new file. We do not have to break our commits right down - we can have lots of staged files in one commit - we just want to keep our commits to be based on one main idea.

It is best to keep our commits atomic since it is easier to fix problems if we do so without messing up other changes which we might want to keep.

### Amending Commits

We can use the `--amend` option to amend the previous commit - it will not work on any other commits.

We might for example have forgotten to stage a file - we can use `git add missed_file.txt` to stage it and then use `git commit --amend` to amed the previous commit rather than adding a new one.

We can amend our previous commit message using `git commit --amend` without doing anything else.

### Ignoring Commits

If we want git to not track directories or files inside a repo - for example api keys, credentials, log files or dependencies - we can use a `.gitignore` file.

We can place the `.gitignore` file anywhere inside the repo but it is best to place it in the root. We can now add entries to the file.

In order to get git to ignore files we can use `file_to_ignore`

In order to get git to ignore directories we can use `dir_to_ignore/` The end `/` specifies it is a directory.

We can also use *wildcards* as usual.

## Branching

Branches are important as they let is work on different ideas related to a project and what we do on one branch will not impact other branches of the same project until we merge them.

This means that branches are essentialy different timelines for a project.

### Master Branch

The *master branch* is the *main branch*. This is the default branch and it is the same as any other branch.

The *main branch* is often used as the branch on which the main version of a project is kept and therefore we do not commit directly to the main branch - we want to avoid messing it up.

This means we can create a *feature branch* when we want to develop something on our project before merging it back to the *main branch*.

#### HEAD -> master

*HEAD* is a pointer which refers to our current location in a repo.

It can refer to the latest commit which has been made on the *master* branch, but it can be moved to refer to different locations.

This means that *HEAD* refers to what is open in our repo - what we are working on at a point in time.



### Viewing Branches

We can list all current branches in a repo by using `git branch` The currently active branch will have `*` next to it.

### Creating New Branches

We use `git branch name-of-branch` to create a new branch. This command creates a new branch but it does not switch to it.

### Switching Branches

We can switch to a different branch using `git switch name-of-branch`

When we switch to a different branch, HEAD will refer to the new branch.

We can create a new branch and switch to it using `git switch -c name-of-branch`

>[!NOTE]
>We might see `git checkout` used to switch branches - this is the older way to do it

#### Unstaged Changes

We will get an error message if we try to switch branches when we have changes on the current branch which have not been commited.

If we have an untracked change then we can switch branches - it will follow us to the new branch.

### Deleting Branches

We cannot delete a branch if we are on it (checking it out) so we will need to switch to a different branch first.

If the branch we want to delete is fully merged we can use `git branch -d old-branch`

If the branch we want to delete has not been fully merged, we can force the deletion using `git branch -D old-branch` but we need to be careful so we do not lose work which we want to keep.

### Renaming Branches

We can rename a branch using `git branch -m new-name` whilst we are on the branch which we want to rename. The `-m` flag refers to `move` as used in linux.

### Merging Branches

We will want to merge work done on one branch to another branch at some point. This might be as simple as after having worked on a feature branch - and the feature has been approved - we want to merge the feature branch back onto the main branch.

There are two guiding principles with merging:

1. We merge branches rather than individual commits
2. We always merge to the current HEAD branch - the branch we are on

This means that a simple way to merge branches is as follows:

1. Switch to the receiving branch - the branch we want to merge into
2. Use the `git merge` command to merge changes from a specified branch into the current branch

We might be on a branch called `scoring` and we have completed our work on it. We want to merge our changes into `main` First of all, we will use `git switch main` We will then use `git merge scoring`

This is a simple way to merge - it works off the premise that no other changes have occured on the main branch. In essence, we are just getting the main branch to catch up with the feature branch - this is known as a *fast forward merge*

## Github

### Existing Repo to Github

If we have an existing repo on our local machine which does not yet exist on github we first of all need to create a new repo on github.

We then let the local repo know about the github repo before pushing code from it onto the new github repo.

#### Git Remotes

Before we push anything to github we need to tell git about our remote repo on github. This is essentially a destination which git will push code to. Each remote (destination) is a URL where a repo can be found.

To see existing remotes for a repo we can use `git remote` or `git remote -v` for more verbose output.

The *origin* will be the remote repo.

Since we are using a local repo which does not yet have a connection to a remote repo we will need to create a connection. We can do this using `git remote add origin https://github.com/zigzaga00/new-repo`

The `origin` part is the label for the remote repo - we could change this to anything we want but *origin* is most commonly used by convention.

### Starting From Scratch

If we have not started work on a project we can create a repo on github, clone it, work on it and then push changes back to github. We can do this with existing repos on github, too.

