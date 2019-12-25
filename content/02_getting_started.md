---
layout: default
title: Git basics
parent: Outline
nav_order: 2
---

## Git basics

One of the challenges of learning Git is becoming familiar with its terminology and command structure. Git commands consist of verbs such as `add`, `commit`, and `push` preceded by the word `git`.  These base commands are often followed by options that provide more information about how and where Git should act.

The best way to learn a langauge is through practice.  In this workshop we will use Git to setup a new version-controlled project.

### Creating a repository

You can think of a **repository** as a group of files that Git tracks.  When you create a repository Git generates a hidden directory named `.git` in the same folder. Information about the repository, changes to the files, and previous versions are all stored in this hidden directory so they are accessible but don't get in the way.

You can create repositories using [GitHub's web interface](https://github.com/new), or on your own computer using the command line.  Let's use the command line to create a Git repository for new project.

First, create a directory called `hello-world` and navigate to the new directory.

Input
{: .label .label-green}
~~~
$ mkdir hello-world
$ cd hello-world
~~~

If you're not sure you're in the right place use the command "pwd" (print working directory) to display the complete path of your current directory.
{: .info}

We will now create a Git repository to track changes to our project.  Use the git **init** command, 
which is simply short for *initialise*.

Input
{: .label .label-green}
~~~
$ git init
~~~
Output
{: .label .label-yellow}
~~~---
title: "Getting started with git"
teaching: 20
exercises: 0
questions:
- "What are repositories and how are they created?"
- "What do `add` and `commit` mean?"
- "How do I check the status of my repository?"
objectives:
- "create a git repository"
- "track changes to files using the git repository"
- "query the current status of the git repository"
keypoints:
- "Git repositories contain metadata about files under version control"
- "This metadata enables us to track changes to files over time"
- "Git uses a two-stage commit process. Changes to files must first be added to the staging area, then committed to the repository"
---

### Using Git

One of the main barriers to getting started with git is the language. Although some of the language used in git is 
fairly self-explanatory, other terms are not so clear. The best way to get to learn the language - which consists of a 
number of verbs such as `add`, `commit` and `push` (preceded by the word 'git') - is by using it, which is what we will be doing during this 
lesson. These commands will be explained as we proceed from setting up a new version-controlled project to publishing 
our own website.


### Creating a repository

A Git **repository** is a data structure used to track changes to a set of project files over time. Repositories are 
stored within the same directory as these project files, in a hidden directory called `.git`. We can create a new git 
repository either by using [GitHub's web interface](https://github.com/new), or via the command line. Let's use the command line to create a git 
repository for the experiments that we're going to do today.

First, we will create a new directory for our project and enter that directory.
<!explain commands as we go along>

~~~
$ mkdir hello-world
$ cd hello-world
~~~
{: .bash}

We will now create an empty git repository to track changes to our project. To do this we will use the git **init** command, 
which is simply short for *initialise*.

~~~
$ git init
~~~
{: .bash}
~~~
Initialized empty Git repository in <your file path>/hello-world/.git/
~~~
{: .output}


The `hello-world` directory is now a git repository. 

If we run the `ls` command now (`ls` lists the content of the `hello-world` 
directory), the repository might seem empty; however, adding the `-a` flag 
for all files via `ls -a` will show all hidden files, which in this case 
includes the new hidden directory `.git`.

Note that whenever we use git via the command line, we need to preface each command (or verb) with `git`, so that the computer knows 
we are trying to get git to do something, rather than some other program.

### Displaying the current project's status

We can run the `git status` command to display the current state of a project. Let's do that now.

~~~
$ git status
~~~
{: .bash}
~~~
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
~~~
{: .output}

The output tells us that we are on the master branch (more on this later) and that we have nothing to commit (no 
unsaved changes).


### Adding and committing

We will now create and save our first project file. This is a two-stage process. First, we **add** any files for which 
we want to save the changes to a staging area, then we **commit** those changes to the repository. This two-stage 
process gives us fine-grained control over what should and should not be included in a particular commit.

Let's create a new file using the `touch` command, which is a quick way to create an empty file.

~~~
$ touch index.md
~~~
{: .bash}

The `.md` extension above signifies that we have chosen to use the Markdown format, a lightweight markup language with plain text formatting syntax. We will explore Markdown a bit later.

Let's check the status of our project again.

~~~
$ git status
~~~
{: .bash}
~~~
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.md

nothing added to commit but untracked files present (use "git add" to track)
~~~
{: .output}

This status is telling us that git has noticed a new file in our directory that we are not yet tracking. With colourised 
output, the filename will appear in red. To change this, and to tell Git we want to track any changes we make to 
index.md, we use `git add`.

~~~
$ git add index.md
~~~
{: .bash}

This adds our Markdown file to the **staging area** (the area where git checks for file changes). To confirm this we want to use `git status` again.

~~~
$ git status
~~~
{: .bash}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   index.md
~~~
{: .output}

If we are using colourised output, we will see that the filename has changed colour (from red to green). Git also tells us that there
is a new file to be committed but, before we do that, let's add some text to the file.

We will open the file `index.md` with any text editor we have at hand (e.g. Notepad on Windows or TextEdit on Mac OSX) and enter `# Hello, world!`. The
hash character is one way of writing a header with Markdown. Now, let's save the file within the text editor and check if Git
has spotted the changes.

~~~
$ git status
~~~
{: .bash}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.md
~~~
{: .output}

This lets us know that git has indeed spotted the changes to our file, but that it hasn't yet staged them, so let's add 
the new version of the file to the staging area.

~~~
$ git add index.md
~~~
{: .bash}

Now we are ready to  **commit** our first changes. 
Commit is similar to 'saving' a file to Git. 
However, compared to saving, a commit provides a lot more information about the changes we have made,
and this information will remain visible to us later.


~~~
$ git commit -m 'Add index.md'
~~~
{: .bash}
~~~
[master (root-commit) e9e8fd3] Add index.md
 1 file changed, 1 insertion(+)
 create mode 100644 index.md
~~~
{: .output}

We can see that one file has changed and that we made one insertion, which was a line with the text '#Hello, world!'. 
We can
also see the commit message 'Add index.md', which we added by using the `-m` flag after `git commit`.
The commit message is used to record a short, descriptive, and specific summary of what we did to help us remember later on without having to look at the actual changes.
If we just run `git commit` without the `-m` option, Git will launch nano (or whatever other editor we configured as `core.editor`)
so that we can write a longer message.

Having made a commit, we now have a permanent record of what was changed,
along with metadata about who made the commit and at what time.

> ## More on the Staging Area
>
> If you think of Git as taking snapshots of changes over the life of a project,
> `git add` specifies *what* will go in a snapshot
> (putting things in the staging area),
> and `git commit` then *actually takes* the snapshot, and
> makes a permanent record of it (as a commit).
> If you don't have anything staged when you type `git commit`,
> Git will prompt you to use `git commit -a` or `git commit --all`,
> which is kind of like gathering *everyone* for the picture!
> However, it's almost always better to
> explicitly add things to the staging area, because you might
> commit changes you forgot you made. (Going back to snapshots,
> you might get the extra with incomplete makeup walking on
> the stage for the snapshot because you used `-a`!)
> Try to stage things manually,
> or you might find yourself searching for "git undo commit" more
> than you would like!
{: .callout}

![The Git Staging Area](../fig/git-staging-area.svg)

At the moment, our changes are only recorded locally, on our computer. If we wanted to 
work collaboratively with someone else they would have no way of seeing what we've done.
We will fix that in the next episode by using GitHub to share our work.

Initialized empty Git repository in <your file path>/hello-world/.git/
~~~

Your `hello-world` directory is now a git repository. 

If you run the "ls" command to list the contents of the "hello-world" 
directory your repository may seem empty.  But running "ls -a" instead will include hidden files in the list, revealing the new hidden directory named ".git".
{: .info}


### Displaying project status

The `git status` command displays the current state of a project.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
~~~

The output introduces two new Git concepts:
- **branch master**. A Git repository can be split into multiple "branches" that can be worked on independently before merging later. New repositories start with only one branch, named "master" by default. In this workshop everything we do is will be in branch master.
- **commit**. The `git commit` command saves your changes to the repository. The output above tells us there is nothing new to save in our repository.


### Adding and committing

We will now create and save our first project file. This is a two-stage process. First, we **add** any files for which 
we want to save the changes to a staging area, then we **commit** those changes to the repository. This two-stage 
process gives us fine-grained control over what should and should not be included in a particular commit.

Let's create a new file using the `touch` command, which is a quick way to create an empty file.

Input
{: .label .label-green}
~~~
$ touch index.md
~~~


The `.md` extension is for text files written using Markdown, a lightweight markup language with plain text formatting syntax. For more on Markdown see (link to Markdown resource, add .md cheatsheet to resources list)

Let's check the status of our project again.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.md

nothing added to commit but untracked files present (use "git add" to track)
~~~

Git has noticed a new file in our directory that we are not yet tracking. With colourised 
output, the filename will appear in red. To change this, and to tell Git we want to track any changes we make to 
index.md, we use `git add`.

Input
{: .label .label-green}
~~~
$ git add index.md
~~~


This adds the file to the **staging area**, telling Git that "index.md" is a file it should track. To see what effect this had we can use `git status` again.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   index.md
~~~


The "index.md" file now appears under "changes to be committed."  If you are using colourised output in your terminal the filename may have changed colour from red to green.

Before committing the new file, open "index.md" in a text editor, add a line of text, then save the file. (In this example we enter the text `Hello, world!`). Use `git status ` to see what has chnaged from Git's perpective.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.md
~~~


This lets us know that Git has indeed spotted the changes to our file, but that it hasn't yet staged them, so let's add 
the new version of "index.md" to the staging area.

Input
{: .label .label-green}
~~~
$ git add index.md
~~~


Now we are ready to  **commit** our first changes. Commit is similar to "saving" a file, but in addition to saving the _contents_ of a file `git commit` stores information about the file's history, including what changes were made, when, and by whom.

Input
{: .label .label-green}
~~~
$ git commit -m 'Add index.md'
~~~

Output
{: .label .label-yellow}
~~~
[master (root-commit) e9e8fd3] Add index.md
 1 file changed, 1 insertion(+)
 create mode 100644 index.md
~~~


We can see that one file has changed and that we made one insertion, which was a line with the text '#Hello, world!'. 
We can also see the commit message 'Add index.md', which we added by using the `-m` flag after `git commit`.
The commit message is used to record a short, descriptive, and specific summary of what we did to help us remember later on without having to look at the actual changes.

If we just run `git commit` without the `-m` flag Git will launch a text editor so we can write a longer message describing the commit.
{: .info}

Having made a commit, we now have a permanent record of what changed,
along with information about who made the commit and at what time.

## Here's another perspective at the "Staging Area"

If you think of Git as taking snapshots of changes over the life of a project, `git add` specifies *what* will go in a snapshot (putting things in the staging area), and `git commit` then *actually takes* the picture and makes a permanent record of it (as a commit). If you don't have anything staged when you type `git commit`, Git will prompt you to use `git commit -a` or `git commit --all`.  This will automatically stage *and* commit all changes to all files in your repository at once, so use this option with caution. 

![The Git Staging Area](figures/git_staging_area.svg)

