# git learn --mode=fast

## Version Control
A version control system or VCS, also known as revision control or source control system, is a software utility that **tracks** and **manages** changes to a filesystem. A VCS also offers collaborative utilities to **share** and **integrate** these filesystem changes to other VCS users.
>Popular software industry VCS options include Git, Mercurial, SVN and preforce. Here we will focus on `Git`.

##Git vs Github
Git is **not** Github. Haven't trust me?

```javascript
if("Git" == "Github"){
console.log("Code lies.");
} else {
coneole.log("Code never lies.");
{
>Code never lies.
```
**Git** allows groups of people to work on the same documents (often code) at the same time, and without stepping on each other's toes. It's a [distributed] (https://en.wikipedia.org/wiki/Distributed_version_control) version control system.
**Github** is just a place to store your identical working directories - aka repositories, or repo's for short. It's literally a hub for Git repositories.

##Installing Git
To install Git, go to the [official website](https://git-scm.com/download) and download the executable for your machine. I'm not going into the installation details as they're really just a bunch of `Next, Next, Next, Finish` set of steps.

To make sure your installation was successful, run the following command in your Terminal/Command prompt:
`git --version`
You should get something like:
`git version 2.15.1`

## Let's Start
First of all, make an empty directory. Open terminal/command prompt(Git Bash will be a great choice) and make sure that your current working directory is newly created one.
To initialize a Git repository here, type the following command:
```terminal
git init
```
>Repository is a directory where Git has been initialized to start version controlling your files.

Notice a new hidden directory `.git`. It has all sorts of directories and files inside it. You'll rarely ever need to do anything inside here but it's the guts of Git, where all the magic happens.

Next up, let's type the `git status` command to see what the current state of our project is:
```terminal
git status
```
It's healthy to run `git status` often. Sometimes things change and you don't notice it.
>staged:
Files are ready to be committed.
unstaged:
Files with changes that have not been prepared to be committed.
untracked:
Files aren't tracked by Git yet. This usually indicates a newly created file.
deleted:
A file has been deleted and is waiting to be removed from Git.

Suppose you have created a new file, let's say it demo.txt. Git will output that "demo.txt is `untracked`".
To tell Git to start tracking changes made to demo.txt, we first need to add it to the **Staging Area** by using:
```terminal
git add demo.txt
```
>Staging Area:
A place where we can group files together before we "commit" them to Git.

Let's run `git status` again to see where we stand.
Notice how Git says changes to be `committed`? The files listed here are in the Staging Area, and they are not in our repository yet. We could add or remove files from the stage before we store them in the repository.

>add all:
You can also type `git add -A .` where the dot stands for the current directory, so everything in and beneath it is added. The -A ensures even file deletions are included.
git reset:
You can use git reset <filename> to remove a file or files from the staging area.

To store our staged changes we run the commit command with a message describing what we've changed. Let's do that now by typing:

```terminal
git commit -m "initial commit"
```
>Commit
A "commit" is a snapshot of our repository. This way if we ever need to look back at the changes we've made (or if someone else does), we will see a nice timeline of all changes.

So we've made a commit. Now let's browse them to see what we changed. We can do this by typing:
```terminal
git log
```
>Git's log as a journal that remembers all the changes we've committed so far, in the order we committed them. Use `git log --summary` to see more information for each commit.


Clap for your self. You are doing great. Now, let us move to the next level.

##Cloning a repository
In your organisation you will be provided with a link, which looks similar to this:
` https://github.com/9kWorld/demoMain.git`
We are going to get this repository to our computer. This can be done by typing:
```terminal
git clone https://github.com/9kWorld/demoMain.git
```
Now, you have a new folder `demoMain`.

Remember, you shouldn't commit to master, **EVER**?

##Branching

**Branches** are what naturally happens when you want to work on multiple features at the same time. You wouldn't want to end up with a `master` branch which has Feature A half done and Feature B half done.
Rather you'd separate the code base into two "snapshots" (branches) and work on and commit to them separately. As soon as one was ready, you might merge this branch back into the master branch and push it to the remote server.
>Master branch is the main of all other branches(if present).

Let's create a branch called `demoBranch`, where we'll do all the work:
```terminal
git branch demoBranch
```
Great! Now if you type `git branch` you'll see two local branches: the main branch named `master` and your new branch named `demoBranch`.
You can switch branches using the `git checkout <branch>` command. Try it now to switch to the `demoBranch` branch:
```terminal
git checkout demoBranch
```
>Try `git checkout -b new_branch`
to checkout and create a branch at the same time. This is the same thing as doing:
`git branch new_branch
 git checkout new_branch`

Change whatever you have to do, fix bugs or add a new feature.
Feel free to run `git status` to check the changes you're about to commit.

Now, you are ready to commit your changes.
`git commit -m "your message here"`

Great, now you just need to switch back to the `master` branch so you can copy (or merge) your changes from the `demoBranch` branch back into the `master` branch.
Go ahead and checkout the master branch:
```terminal
git checkout master
```
Alrighty, the moment has come when you have to merge your changes from the demoBranch branch into the master branch. Take a deep breath, it's not that scary.

We're already in the `master` branch, so we just need to tell Git to `merge` the `demoBranch` branch into it:
```terminal
git merge demoBranch
```
**Merge Conflicts** can occur when changes are made to a file at the same time. A lot of people get really scared when a conflict happens, but fear not! They aren't that scary, you just need to decide which code to keep. Take a look at [how conflicts are presented](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented).

You can use `git branch -d <branch name>` to delete a branch if you don't need it anymore. Use `--force(-f)` delete option to delete a branch if it has not been merged yet. This also can be done by:
 `git branch -D wrong_feature`

##The Final Push
Here we are, at the last step.All that's left for you to do now is to push everything you've been working on to your remote repository, and you're done!
```terminal
git push
```
Finally, we did it.

Hope this helped! Good luck.

https://dev.to/prnaav9k/git-learn---modefast-2bpl

